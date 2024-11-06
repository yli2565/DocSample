---
layout: default
title: "PYLogReader"
parent: "Code"
---
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

{: .caution}
The [Option 1](#option-1-small-logs--1gb) is broken by some update, please don't use it now

# PYLogReader

This is a Python repo to read binary log from BHuman. Intend to be faster and easier to manipulate the log data.

There's an easy to use [CLI version](https://github.com/wistex-united/py-log-reader/blob/master/LogReaderCLI.py) for dumping log into json and png, but you can also use the Log Interface to access the data directly. The binary log from BHuman is much more compressed then json and would be much faster to be directly read.

## CLI Version

[CLI script](https://github.com/wistex-united/py-log-reader/blob/master/LogReaderCLI.py)

```
usage: LogReaderCLI.py [-h] [--numworkers NUMWORKERS]
                       [--threads {Upper,Lower,Motion,Audio,Cognition,Referee} [{Upper,Lower,Motion,Audio,Cognition,Referee} ...]]
                       [--start-time START_TIME] [--end-time END_TIME]
                       [--start-frame START_FRAME] [--end-frame END_FRAME] [--profile]
                       inputFile
Parallel log file processor

positional arguments:
  inputFile             Input log file path

options:
  -h, --help            show this help message and exit
  --numworkers NUMWORKERS
                        Number of worker processes (default: CPU count)
  --threads {Upper,Lower,Motion,Audio,Cognition,Referee} [{Upper,Lower,Motion,Audio,Cognition,Referee} ...]
                        List of threads to process (default: all frames)
  --start-time START_TIME
                        Start time in format hour:min:sec.millisecond, sec is mandatory, others
                        are optional
  --end-time END_TIME   End time in format hour:min:sec.millisecond, sec is mandatory, others are
                        optional
  --start-frame START_FRAME
                        Start frame number
  --end-frame END_FRAME
                        End frame number
  --profile             Enable performance profiling

Examples:
  # Basic usage with defaults
  LogReaderCLI.py input.log
  
  # Specify number of workers and threads
  LogReaderCLI.py input.log --numworkers 4 --threads Upper Lower
  
  # Process time range
  LogReaderCLI.py input.log --start-time 0:00:00.000 --end-time 1:30:00.000
  
  # Process frame range
  LogReaderCLI.py input.log --start-frame 1000 --end-frame 2000
  
  # Enable profiling
  LogReaderCLI.py input.log --profile
```

## Log Interface

### Log File Hierarchy

{: .info}
It would be very helpful for you to browse through the hierarchy before working with log data

![log-file-hierarchy.svg](./log-file-hierarchy.svg){: .responsive-graph-medium}

For more details, please refer to [BHuman logging doc](https://docs.b-human.de/coderelease2024/architecture/logging/)

### LogInterfaceBaseClass

Purely abstract class, define the shared interface for all log classes

Some important attributes:

- `parent`: Reference to containing object
   - Frames reference UncompressedChunk
   - Messages reference Frame
   - Used for hierarchy traversal

- `children`: List of contained objects
   - UncompressedChunk contains Frames
   - Frames contain Messages
   - Used for iteration and tree structure

- `log`: Reference to root Log object
   - Quick access to global log state
   - Caches common data
   - Access to Chunks like TypeInfo, MessageID

- `startByte`: Starting byte position in log file
   - Used for reading data
   - Defines object boundaries

- `endByte`: Ending byte position in log file
   - Used for reading data
   - Defines object boundaries

- `index`: Relative position in parent's children
   - Frame 5 in UncompressedChunk
   - Message 3 in Frame 5

- `absIndex`: Absolute position in log file
   - Unique identifier across entire log
   - Used for caching and lookups

### LogInterfaceAccessorClass vs LogInterfaceInstanceClass

There are two kinds of interface, accessor and instance, which are very different but interchangeable holder of data.

The root log object and all chunk objects are always instance class, while message and frame objects can be either accessor or instance.

| Aspect | LogInterfaceAccessorClass | LogInterfaceInstanceClass |
|--------|----------|----------|
| **Purpose** | Used for efficient memory access in large log files | Used for complete in-memory representation |
| **Memory Usage** | Light-weight, only loads data on demand | Heavier, keeps all data in memory |
| **Parent Resolution** | Deduces parent through index information | Directly stores parent reference |
| **Mutability** | Can be frozen to prevent index changes | Frozen by default |
| **Index Setting** | Can change index to access different data | Fixed index, cannot be changed |
| **Data Access** | Uses memory mapped file for on-demand loading | Direct access to parsed data |
| **Caching** | Caches data in Log class | Store data in instance itself |
| **Children Handling** | Creates children accessor on demand | Stores children instances directly |
| **Serialization** | Stores minimal state (mainly indices) | Stores complete object state |
| **Parsing Strategy** | Parse-on-demand (lazy loading) | Parse-all-at-once (eager loading) |
| **Memory Trade-off** | Lower memory, higher disk I/O | Higher memory, lower disk I/O |

{: .attention}
All accessor objects are created by root log object with `getMessageAccessor` or `getFrameAccessor` and it have more reliance on root log object than its parent.

{: .info}
Accessor itself is a iterator that can iterate on a predefined range. You can pass the range as `indexMap` arg to `getMessageAccessor` or `getFrameAccessor` when you create the accessor.

### Threads

Thread is not a layer of abstraction, it is just a collection of Frames. Now it is implement as a Frame accessor iterating on frames from specific thread.

You can get it by `UncompressedChunk.thread("<ThreadName>")`

## Using the Log Interface

### Basic Setup

First, create and initialize a Log object:

```python
from LogInterface import Log

# Create log object
log = Log()

# Read the log file
log.readLogFile("path/to/your/log.log")
```

### Preprocessing Options

{: .caution}
The [Option 1](#option-1-small-logs--1gb) is broken by some update, please don't use it now

There are two main approaches to preprocessing the log file, depending on its size:

#### Option 1: Small Logs (< 1GB)
For smaller logs, you can load everything into memory:

```python
# Full preprocessing - loads everything into memory
log.eval()        # Evaluate log structure
log.parseBytes()  # Parse all messages

# Now all frames and messages are instance classes
# Full random access, but higher memory usage
```

#### Option 2: Large Logs (≥ 1GB)
For larger logs, use memory-efficient accessor mode:

```python
# Memory-efficient preprocessing
log.eval(isLogFileLarge=True)  # Creates index file for efficient access

# Get frame accessor for iterating through frames
frame_accessor = log.getFrameAccessor()

# Optional: limit range of frames
specific_frames = log.getFrameAccessor(range(1000, 2000))  # Frames 1000-1999
```

### Accessing Representations

Each frame contains various representations (data objects) that can be accessed in multiple ways:

```python
# Get a frame (either from accessor or instance)
frame = log.getFrameAccessor()[0]  # First frame

# 1. Direct access by representation name
robot_pose = frame["RobotPose"]              # Get RobotPose representation
camera_matrix = frame["CameraMatrix"]        # Get CameraMatrix representation

# 2. Check if representation exists
if "BallPercept" in frame:
    ball = frame["BallPercept"]

# 3. Access multiple representations
representations = ["RobotPose", "BallPercept", "TeamData"]
for repr_name in representations:
    try:
        data = frame[repr_name]
        print(f"{repr_name}: {data}")
    except KeyError:
        print(f"{repr_name} not found in frame")

# 4. Special case: Annotations (can have multiple per frame)
annotations = frame.Annotations  # Returns list of all annotations
```

### Error Handling

```python
try:
    # Access a representation
    frame["RobotPose"]
except KeyError as e:
    # Handle missing representation
    print(f"Representation not found: {e}")

# For optional representations
ball_percept = frame["BallPercept"] if "BallPercept" in frame else None
```

### Memory Considerations

- Instance mode (small logs):
  - Pros: Faster repeated access, simpler operation
  - Cons: High memory usage (approximately 15x log file size)

- Accessor mode (large logs):
  - Pros: Memory efficient, suitable for large logs
  - Cons: Slightly slower access, needs index file

### Performance Tips

1. Choose the appropriate preprocessing mode based on log size
2. Use frame ranges when you don't need the entire log
3. Cache frequently accessed representations
4. Use thread-specific accessors when working with single threads
   ```python
   # Get frames only from Cognition thread
   cognition_frames = log.UncompressedChunk.thread("Cognition")
   ```
5. If possible, you can use multiprocessing to speed up your work, pleas refer to the CLI script

### Common Patterns

```python
# Process frames in batches
frame_accessor = log.getFrameAccessor()
for frame in frame_accessor:
    # Access common representations
    if "RobotPose" in frame:
        robot_pose = frame["RobotPose"]
        # Process robot pose data
        
    # Handle optional representations
    ball_data = frame["BallPercept"] if "BallPercept" in frame else None
    if ball_data:
        # Process ball data
        
    # Work with multiple annotations
    for annotation in frame.Annotations:
        # Process each annotation
```
