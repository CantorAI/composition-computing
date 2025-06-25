# Cantor Host - XLang APIs

The `Cantor Host` class provides several APIs that can be accessed through XLang for interacting with data views, frames, and runtime operations. These APIs are designed to be used either inside the Cantor process (directly imported) or from a standalone process (using shared memory for remote access).


## Getting Started

Before using any APIs, create an instance of the host object:
```xlang
host = cantor.Host()
```

---

## Methods

### `PushFrame`
Pushes a data frame into the system.

#### API Signature
```xlang
host.PushFrame(frame: DataFrame, priority: int = 2) -> bool
```

#### Description
- Pushes a `DataFrame` into the system with an optional priority.
- Default priority is `2`.

---

### `PopFrame`
Pops a data frame from a specific data view.

#### API Signature
```xlang
host.PopFrame(dvId: DataViewID, ts: TimeStamp, timeout_ms: int) -> DataFrame
```

#### Description
- Retrieves a `DataFrame` from the specified data view ID.
- Returns an empty value if no frame is available within the timeout.

---

### `CreateDataView`
Creates a new data view with a specified filter.

#### API Signature
```xlang
host.CreateDataView(filter: str) -> DataViewID
```

#### Description
- Creates a `DataView` based on the given filter string.
- Returns the `DataViewID` for the created view.

---

### `RemoveDataView`
Removes a data view by ID.

#### API Signature
```xlang
host.RemoveDataView(dvId: DataViewID) -> bool
```

#### Description
- Removes the `DataView` identified by the given `DataViewID`.
- Returns `True` if successful, otherwise `False`.

---

### `generate_uid`
Generates a unique identifier.

#### API Signature
```xlang
host.generate_uid() -> str
```

#### Description
- Generates a globally unique identifier (GUID).

---

## Properties

### `NodeId`
Gets or sets the Node ID of the Cantor host.

#### API Access
```xlang
host.NodeId
```

#### Description
- **Getter:** Returns the current Node ID as a string.
- **Setter:** Sets the Node ID using a string.

---

### `NodeName`
Gets or sets the Node Name of the Cantor host.

#### API Access
```xlang
host.NodeName
```

#### Description
- **Getter:** Returns the current Node Name as a string.
- **Setter:** Sets the Node Name using a string.

---

## Additional Notes

1. **Shared Memory Connection:**
   - If the `CantorHostImpl` is accessed from a standalone process (not running within the Cantor process), it will use Cantor's **shared memory method** to enable a fast remote connection.
   - If accessed inside the Cantor process, the APIs operate directly without using shared memory.

2. **Data View Management:**
   - Data views allow for efficient handling of data frames with support for filtering and priority-based insertion.
   - APIs like `CreateDataView`, `RemoveDataView`, `PushFrame`, and `PopFrame` provide a comprehensive interface for managing data views.

3. **Multithreading:**
   - All APIs are thread-safe, ensuring proper synchronization when accessing or modifying shared resources like data views.

```