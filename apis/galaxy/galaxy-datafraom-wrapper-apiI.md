# GalaxyDataFrameWrapper API

This document provides the API documentation for the `GalaxyDataFrameWrapper` class, including all available properties and methods. This class is a wrapper for data frame handling in the Galaxy system, designed for data transport and binary exchange.

---

## Class: `GalaxyDataFrameWrapper`

**Description**: A wrapper class for handling binary data frames in Galaxy. Inherits from `GalaxyDataFrame` and provides methods to access metadata (header), binary content, and formatted transformations (e.g., ndarrays).

**Usage**:
```python
df = cantor.GalaxyDataFrame()
```

---

## Properties

### `type`
**Description**: Specifies the frame type using a numeric value or string format.

**Usage**:
```python
df.type = "divx"
type_code = df.type
```

---

### `NodeId_High`, `NodeId_Low`
**Description**: Unique identifier for node ID split across two fields.

**Usage**:
```python
high = df.NodeId_High
low = df.NodeId_Low
```

---

### `startTime`
**Description**: Time when the frame began processing or was captured.

**Usage**:
```python
df.startTime = timestamp
```

---

### `format1` to `format8`
**Description**: Format metadata (e.g., dimensions, pixel size) stored as eight fields.

**Usage**:
```python
df.format1 = 1920
height = df.format2
```

---

### `dataSize`
**Description**: Indicates the size of the data buffer in bytes.

**Usage**:
```python
size = df.dataSize
```

---

### `data`
**Description**: Raw binary data stored in the data frame.

**Usage**:
```python
df.data = binary_blob
```
**Details**: Accepts a binary value or a serializable object, which is internally converted.

---

## Methods

### `GetHead`
```python
def GetHead() -> bytes:
    """Returns the binary representation of the data frame header."""
```
**Usage**:
```python
header = df.GetHead()
```

---

### `GetData`
```python
def GetData() -> bytes:
    """Returns the binary content of the data field."""
```
**Usage**:
```python
payload = df.GetData()
```

---

### `GetString`
```python
def GetString() -> str:
    """Returns the data as a UTF-8 string. Logs the string to console."""
```
**Usage**:
```python
text = df.GetString()
```

---

### `GetHeadAndData`
```python
def GetHeadAndData() -> List[bytes, bytes]:
    """Returns a list with header and data binaries."""
```
**Usage**:
```python
head, data = df.GetHeadAndData()
```

---

### `ToNdarray`
```python
def ToNdarray() -> ndarray:
    """Converts the frame into a 3D NumPy ndarray using width, height, and pixel size."""
```
**Usage**:
```python
array = df.ToNdarray()
```
**Details**: Assumes format1 = width x height, format2 = pixel size.

---

### `To1DNArray`
```python
def To1DNArray() -> ndarray:
    """Converts raw data into a 1D NumPy array."""
```
**Usage**:
```python
array = df.To1DNArray()
```

