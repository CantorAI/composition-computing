
---

# Cantor Network - XLang APIs Documentation

The `Cantor Network` class provides a simplified interface to manage networking operations such as starting/stopping servers, connecting to servers, and handling networking events.

---

## Getting Started

Before using any APIs, create an instance of the `Network` class:
```xlang
network = cantor.Network()
```

---

## Methods

### `StartServer`
Starts a server to accept client connections.

#### API Signature
```xlang
network.StartServer(port: int, maxConn: int) -> bool
```

#### Description
- Starts a server on the specified `port` with a maximum number of connections (`maxConn`).
- Returns `True` if the server is started successfully, otherwise `False`.

---

### `StopServer`
Stops a server running on a specific port.

#### API Signature
```xlang
network.StopServer(port: int) -> bool
```

#### Description
- Stops the server running on the given `port`.
- Returns `True` if the server is stopped successfully, otherwise `False`.

---

### `Connect`
Establishes a connection to a remote server.

#### API Signature
```xlang
network.Connect(strSrv: str, port: int) -> bool
```

#### Description
- Connects to the remote server identified by `strSrv` (server address) and `port`.
- Returns `True` if the connection is successful, otherwise `False`.

---

## Events

### `OnNewSession`
Triggered when a new session is established.

#### Event Signature
```xlang
network.OnNewSession(session: Dict)
```

#### Description
- This event is fired whenever a new session is established.
- The `session` parameter provides details about the session, such as:
  - `NodeId`: The unique ID of the node in the session.
  - `IP`: The IP address of the node.
  - `Port`: The port number of the session.
  - `isInClientSide`: A boolean indicating if the session is client-side.

#### Example Usage
```xlang
def on_new_session(session):
    print(f"New session established: NodeId={session['NodeId']}, IP={session['IP']}, Port={session['Port']}")

network.OnNewSession += on_new_session
```

---

### `OnConnected`
Triggered when a connection is successfully established.

#### Event Signature
```xlang
network.OnConnected(nodeId: str)
```

#### Description
- This event is fired when the `Connect` method successfully establishes a connection to a node.
- The `nodeId` parameter provides the unique ID of the connected node.

#### Example Usage
```xlang
def on_connected(nodeId):
    print(f"Successfully connected to node: {nodeId}")

network.OnConnected += on_connected
```

---

## Additional Notes

### Thread Safety
- All networking operations and event handling are thread-safe.

### Usage Examples

#### Starting a Server
```xlang
network.StartServer(port=9090, maxConn=100)
```

#### Connecting to a Server
```xlang
network.Connect("192.168.1.100", 9090)
```

#### Handling Events
```xlang
def on_new_session(session):
    print(f"New session: {session}")

def on_connected(nodeId):
    print(f"Connected to: {nodeId}")

network.OnNewSession += on_new_session
network.OnConnected += on_connected
```
