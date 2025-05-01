# Dataset API Reference

This document provides API documentation for the `Dataset` class in the Galaxy namespace, including its methods and properties.

---

## Classes

### `Dataset`
**Description**: A specialized filter used to load datasets from files or folders. It reads data and sends it out via an output pin, commonly used as a source node in a data pipeline.

**Usage**:
```python
dataset = cantor.Dataset()
```

Or with parameters:
```python
dataset = cantor.Dataset("libName", "FilterName", factory)
```

---

## Properties

### `fps`
**Description**: Sets the playback or output speed in frames per second.

**Usage**:
```python
# Set FPS value
dataset.fps = 24.0

# Get current FPS
current_fps = dataset.fps
```
**Getter**: Returns the current frame-per-second value (float).  
**Setter**: Updates the FPS setting for the dataset.

---

## Methods

### `AddFolder`
```python
def AddFolder(path: str, filter: str) -> bool:
    """Adds all files matching a filter in the specified folder to the dataset."""
```
**Description**: Scans the provided folder and adds files that match the specified filter string (e.g., "*.jpg").

**Usage**:
```python
dataset.AddFolder("/data/images", "*.jpg")
```
**Details**:
- Adds to an internal list of file paths.
- Returns `True` if the folder is processed successfully.

---

### `AddFile`
```python
def AddFile(path: str) -> bool:
    """Adds a single file to the dataset."""
```
**Description**: Registers a single file to be processed by the dataset.

**Usage**:
```python
dataset.AddFile("/data/images/image1.jpg")
```
**Details**:
- Useful for manually appending specific files.
- Returns `True` if the file is added successfully.

---

