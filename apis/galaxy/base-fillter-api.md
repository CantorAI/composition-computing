# Galaxy Base Filter API Reference

This document provides an overview of the Galaxy Base Filter API, including available classes, properties, and methods. It is auto-generated based on `APISET().AddClass`, `AddPropL`, `AddProp0`, `AddFunc`, and `AddVarFunc` usage within the source code.

---

## Classes

### `Pin`

**Description**: Represents an input or output pin in a filter pipeline. Handles data frames, downstream connections, and optional task-based delivery.

**Usage**:

```python
pin = cantor.Pin()
```

### `BaseFilter`

**Description**: Base class for all filters used in the Cantor pipeline framework. Supports input/output pins, task execution, and serialization.

**Usage**:

```python
filter = cantor.BaseFilter()
```

---

## Properties

### `inputs`

**Description**: List of input pins for the filter.

**Usage**:

```python
input_pins = filter.inputs
filter.inputs = new_value  # No effect
```

**Getter**: Returns a list of input pins.\
**Setter**: Not implemented.

### `outputs`

**Description**: List of output pins for the filter.

**Usage**:

```python
output_pins = filter.outputs
filter.outputs = new_value  # No effect
```

**Getter**: Returns a list of output pins.\
**Setter**: Not implemented.

### `Description`

**Description**: Description text for the filter.

**Usage**:

```python
filter.Description = "This is my filter"
desc = filter.Description
```

**Getter**: Returns the description.\
**Setter**: Updates the description.

### `frameType` (on `Pin`)

**Description**: Format type of the frame (e.g., FourCC/EightCC).

**Usage**:

```python
pin.frameType = "divx"
type_str = pin.frameType
```

**Getter**: Returns the current format type.\
**Setter**: Sets the frame type from a string.

---

## Methods

### `GetPinByIndex`

```python
def GetPinByIndex(index: int) -> Pin:
    """Returns the Pin instance by index."""
```

### `SetRunFunc`

```python
def SetRunFunc(runFunc: Callable) -> bool:
    """Sets the filter's run function."""
```

### `NewInputPin`

```python
def NewInputPin(pinName: str = "input") -> Pin:
    """Creates a new input pin."""
```

### `NewOutputPin`

```python
def NewOutputPin(pinName: str = "output") -> Pin:
    """Creates a new output pin."""
```

### `Start`

```python
def Start() -> bool:
    """Starts the filter."""
```

### `Stop`

```python
def Stop() -> bool:
    """Stops the filter."""
```

### `Pause`

```python
def Pause() -> bool:
    """Pauses the filter (no-op)."""
```

### `Resume`

```python
def Resume() -> bool:
    """Resumes the filter (no-op)."""
```

### `RunAsTask`

```python
def RunAsTask(conditions: Any, *args, **kwargs) -> Task:
    """Executes the filter as a task with given conditions and arguments."""
```

### `GetInputPinCount`

```python
def GetInputPinCount() -> int:
    """Returns number of input pins."""
```

### `GetOutputPinCount`

```python
def GetOutputPinCount() -> int:
    """Returns number of output pins."""
```

### `GetInputPinLayers`

```python
def GetInputPinLayers() -> str:
    """Returns a string representing layer identifiers for input pins."""
```

### `GetPipelineId`

```python
def GetPipelineId() -> str:
    """Returns the unique pipeline ID."""
```
