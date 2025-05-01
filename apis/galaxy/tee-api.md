# Tee API Reference

The `Tee` class in the Galaxy namespace is a filter that duplicates a single input stream into multiple output streams. It is useful for branching data to multiple consumers in a pipeline, much like the Unix `tee` command.

---

## Getting Started

Create a new instance of the `Tee` filter:

```python
tee = cantor.Tee()
```

Or with factory binding:

```python
tee = cantor.Tee("libName", "FilterName", factory)
```

---

## Methods

### NewOutputPin
**Signature**: `tee.NewOutputPin(pinName: str) -> Pin`

**Description**: Creates and returns a new named output pin on the Tee filter.

**Usage**:
```python
out_pin = tee.NewOutputPin("Branch1")
```

**Details**: This allows external components to connect to the new output and receive duplicated frames.

---

## Internal Methods & Behavior (Not Exposed via APISET)

These are runtime methods involved in frame delivery and serialization but are not script-accessible.

### Deliver
**Signature**: `tee.Deliver(frame: X::Value) -> None`

**Description**: Distributes the provided frame to all registered output pins.

**Details**: Updates internal FPS stats as frames are sent.

---

### Run
**Signature**: `tee.Run() -> None`

**Description**: Starts filter execution (typically invoked by the pipeline manager).

**Details**: Part of the internal pipeline lifecycle.

---

### ToBytes / FromBytes
**Signatures**:
```python
tee.ToBytes() -> X::Value
tee.FromBytes(valBin: X::Value) -> bool
tee.ToBytes(stream: XLStream) -> bool
tee.FromBytes(stream: XLStream) -> bool
```

**Description**: Serializes or restores the filter's configuration.

**Details**: Used when saving or cloning the pipeline state.

---

## Notes

- The `Tee` filter is a passive component — it does not alter data but forwards it.
- FPS is tracked using the `Stats` utility to monitor performance.

