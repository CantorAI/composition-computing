# Fermat API

The `Fermat` class in the Galaxy namespace is a specialized filter derived from `BaseFilter`, intended for high-performance frame processing within a pipeline. It supports serialization, runtime control, and interaction with external sources like GStreamer for video data input.

---

## Getting Started

Before using the Fermat filter, you must instantiate it within a Galaxy pipeline:

```python
fermat = cantor.Fermat()
```

Or with parameters:

```python
fermat = cantor.Fermat("libName", "FilterName", factory)
```

---

## Properties

### Pipeline
**Type**: `str`

**Description**: Represents the description or label for the pipeline this filter is associated with.

**Usage**:
```python
fermat.Pipeline = "Main Video Stream"
print(fermat.Pipeline)
```

**Details**: Internally sets or returns `m_strDesc`. Useful for UI or logging purposes.

---

## Methods

The following are internal and overridden methods used primarily for data processing and system integration. While not exposed via `APISET()` for scripting access, they contribute to the overall behavior of `Fermat`.

### ToBytes
**Signature**: `fermat.ToBytes() -> X.Value`

**Description**: Serializes the filter's configuration to a binary format.

**Details**: Used to store or transmit the filter's state.

---

### FromBytes
**Signature**: `fermat.FromBytes(valBin: X.Value) -> bool`

**Description**: Deserializes configuration from a binary format to restore filter state.

**Details**: Reconstructs the filter's settings, likely from persisted or network-transferred data.

---

### Run
**Signature**: `fermat.Run() -> None`

**Description**: Starts the internal execution logic of the filter.

**Details**: This is typically invoked as part of the pipeline runtime and shouldn't be manually called.

---

### OnPreStop
**Signature**: `fermat.OnPreStop() -> None`

**Description**: Hook for handling cleanup or shutdown tasks before the filter stops.

**Details**: Used internally to prepare the filter for stopping.

---

### SetCurrentPath
**Signature**: `fermat.SetCurrentPath(path: str) -> None`

**Description**: Sets the current working directory or file path context.

**Details**: Could influence how resources are loaded or written.

---

### PushData
**Signature**:
```python
fermat.PushData(data: bytes, dataSize: int,
                srcId: int, timestamp: int,
                w: int, h: int, pixSize: int, outFormat: int) -> None
```

**Description**: Accepts new frame data and pushes it into the filter's pipeline for processing.

**Details**: Typically used in callback contexts where external systems (e.g., GStreamer) feed raw data.

---

### QueryNewframe
**Signature**:
```python
fermat.QueryNewframe(buf: bytes, bufSize: int, id: int,
                     width: int*, height: int*, timestamp: int*) -> int
```

**Description**: Used to query a new frame's metadata and buffer.

**Details**: Often called in native/low-level integration scenarios to retrieve video frames.

