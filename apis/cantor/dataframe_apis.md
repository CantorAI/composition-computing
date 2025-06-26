# 5.1.2 Cantor DataFrame - XLang APIs

The `Cantor DataFrame` class provides a comprehensive set of APIs to interact with and manipulate data frames. It includes properties for metadata, formats, and data management, along with functions for accessing and modifying the frame's contents.

## Getting Started

Before using any APIs, create a `DataFrame` instance:
```xlang
frame = cantor.DataFrame(dataSize)
```

---

## Properties

### `type`
Gets or sets the type of the frame.

#### API Access
```xlang
frame.type
```

---

### `startTime`
Gets or sets the start time of the frame.

#### API Access
```xlang
frame.startTime
```

---

### `sourceId`
Gets or sets the source ID of the frame.

#### API Access
```xlang
frame.sourceId
```

---

### `srcAddr`
Gets or sets the source address of the frame.

#### API Access
```xlang
frame.srcAddr
```

---

### `dstAddr`
Gets or sets the destination address of the frame.

#### API Access
```xlang
frame.dstAddr
```

---

### `format1` to `format8`
Gets or sets format-specific metadata for the frame.

#### API Access
```xlang
frame.format1
frame.format2
...
frame.format8
```

---

### `metadata1` to `metadata4`
Gets or sets metadata values associated with the frame.

#### API Access
```xlang
frame.metadata1
frame.metadata2
...
frame.metadata4
```

---

### `refId`
Gets or sets the reference ID of the frame.

#### API Access
```xlang
frame.refId
```

---

### `refIndex`
Gets or sets the reference index of the frame.

#### API Access
```xlang
frame.refIndex
```

---

### `dataSize`
Gets or sets the size of the frame's data.

#### API Access
```xlang
frame.dataSize
```

---

### `dataItemNum`
Gets or sets the number of data items in the frame.

#### API Access
```xlang
frame.dataItemNum
```

---

### `data`
Gets or sets the frame's binary data.

#### API Access
```xlang
frame.data
```

---

## Methods

### `GetHead`
Retrieves the header of the frame.

#### API Signature
```xlang
frame.GetHead() -> Bin
```

#### Description
- Returns the header of the frame as a binary object.

---

### `GetData`
Retrieves the data content of the frame.

#### API Signature
```xlang
frame.GetData() -> Bin
```

#### Description
- Returns the frame's binary data.

---

### `Set`
Sets multiple properties of the frame.

#### API Signature
```xlang
frame.Set(type: str, startTime: int, sourceId: str, ...) -> bool
```

#### Description
- Accepts multiple named parameters (e.g., `type`, `startTime`, `sourceId`, etc.) to set the corresponding frame properties.
- Returns `True` upon successful update.

---

## Additional Notes

1. **Thread Safety:**
   - All operations on the frame are thread-safe to ensure proper synchronization.

2. **Binary Data Handling:**
   - Binary data operations (`GetHead`, `GetData`, `MoveDataToValue`) provide efficient mechanisms for interacting with frame data.

3. **Usage Scenarios:**
   - The `DataFrame` class is versatile, supporting metadata, formats, and binary data manipulation, making it suitable for data-intensive applications.

```