# Player API

The `Player` class in the Galaxy namespace is a frame-synchronization and timing-aware filter that consumes multiple input pins and aligns frames based on timestamp. It is commonly used for synchronized playback or merging of multi-source inputs.

---

## Getting Started

Create a new instance of the `Player` filter:

```python
player = cantor.Player()
```

Or with constructor arguments:

```python
player = cantor.Player("libName", "FilterName", factory)
```

---

## Methods

### NewInputPin
**Signature**: `player.NewInputPin(pinName: str) -> Pin`

**Description**: Dynamically adds a new input pin to the Player filter.

**Usage**:
```python
pin = player.NewInputPin("CameraA")
```

**Details**: This allows the Player to accept frames from an additional source. The pin name is user-defined and must be unique.

---

## Internal Methods & Behavior (Not Exposed via APISET)

These methods are internal to the runtime or used by the host engine, and not meant for scripting access, but they influence the behavior of the filter significantly.

### Run
**Signature**: `player.Run() -> None`

**Description**: Main execution entry point that handles continuous frame processing and synchronization across pins.

---

### CheckAndProcessFrames
**Signature**: `player.CheckAndProcessFrames() -> bool`

**Description**: Checks each pin buffer to determine if synchronized frames are ready and processes them.

**Details**: Called internally during the run loop.

---

### CalcFPS
**Signature**: `player.CalcFPS(frame: X::Value) -> None`

**Description**: Updates internal FPS (frames per second) statistics based on frame arrival timing.

**Details**: Useful for performance diagnostics or output display.

---

### ToBytes / FromBytes
**Signatures**:
```python
player.ToBytes() -> X::Value
player.FromBytes(valBin: X::Value) -> bool
```

**Description**: Serializes and deserializes the filter state for transmission or saving.

**Details**: Uses binary packing to capture runtime configuration.

---

### onPinPutFrame
**Signature**: `player.onPinPutFrame(pin: IPin, frame: X::Value) -> bool`

**Description**: Entry point when a new frame is pushed into the filter.

**Details**: Handles synchronization logic and buffering.

---

### OnPreStop
**Signature**: `player.OnPreStop() -> None`

**Description**: Performs cleanup or finalization just before the filter stops running.

