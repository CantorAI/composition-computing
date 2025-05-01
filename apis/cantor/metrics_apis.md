
---

# Metrics - XLang APIs Documentation

The `Metrics` class provides a comprehensive interface for managing and querying metrics in the Cantor framework. It supports registering, querying, and removing metrics for various objects and instances.

## Getting Started

Before using any APIs, create an instance of the `Metrics` class:
```xlang
metrics = cantor.Metrics()
```

---

## Methods

### `registerMetrics`
Registers a metric with a callback function.

#### API Signature
```xlang
metrics.registerMetrics(object: Any, metrics_key: str, callback_func: Callable) -> bool
```

#### Description
- Registers a metric for the given object with a unique key and a callback function.
- The callback function is executed when the metric is queried.

---

### `removeMetrics`
Removes a registered metric for an object.

#### API Signature
```xlang
metrics.removeMetrics(object: Any, metrics_key: str) -> bool
```

#### Description
- Removes a metric identified by the given key for the specified object.
- Returns `True` if the metric is successfully removed, otherwise `False`.

---

### `queryNodes`
Queries the list of nodes in the system.

#### API Signature
```xlang
metrics.queryNodes() -> List[Dict]
```

#### Description
- Returns a list of nodes as dictionaries, each containing node information.

---

### `queryInstances`
Queries the instances associated with a node.

#### API Signature
```xlang
metrics.queryInstances(nodeId: str) -> List[Dict]
```

#### Description
- Returns a list of instances for the specified node ID.
- Each instance is represented as a dictionary with `Name` and `Id`.

---

### `queryMetricListByInstances`
Queries the list of metrics for specified instances.

#### API Signature
```xlang
metrics.queryMetricListByInstances(nodeId: str, instanceKeys: Any) -> List[Dict]
```

#### Description
- Returns a list of metrics for the provided instances on the specified node.
- Each metric is represented as a dictionary with `Name` and `instanceId`.

---

### `queryMetrics`
Queries a specific metric's value for an object.

#### API Signature
```xlang
metrics.queryMetrics(nodeId: str, object: Any, metrics_key: str) -> Any
```

#### Description
- Retrieves the value of a specific metric for the given object and key.
- Supports querying metrics across nodes.

---

### `SetWordBook`
Sets a metric value in a wordbook for an instance.

#### API Signature
```xlang
metrics.SetWordBook(instanceId: str, word: str, metric: Any) -> bool
```

#### Description
- Stores a metric value under the specified word for the given instance ID.
- Returns `True` if successfully set.

---

### `QueryWordBook`
Queries a metric value from a wordbook for an instance.

#### API Signature
```xlang
metrics.QueryWordBook(instanceId: str, word: str) -> Any
```

#### Description
- Retrieves the value of a metric stored under the specified word for the given instance ID.

---

## Additional Notes

### Metrics Management
1. **Registration:**
   - Metrics can be registered for any object with a unique key and a callback function.
   - The callback can be either a native C++ function or a Python/XLang callable object.

2. **Querying:**
   - Supports querying metrics across nodes, instances, and objects.
   - If the metric is not found locally, the query can be forwarded to remote nodes.

3. **Wordbook:**
   - Provides a key-value storage mechanism for metrics using words and instance IDs.

### Thread Safety
- All operations on metrics, wordbooks, and nodes are thread-safe, ensuring proper synchronization.

### Usage Examples
#### Registering a Metric
```xlang
def my_callback(key):
    return f"Value for {key}"

metrics.registerMetrics(some_object, "cpu_usage", my_callback)
```

#### Querying Metrics
```xlang
value = metrics.queryMetrics("node1", some_object, "cpu_usage")
print(value)
```

#### Removing a Metric
```xlang
metrics.removeMetrics(some_object, "cpu_usage")
```

#### Managing Wordbook
```xlang
metrics.SetWordBook("instance1", "metric1", 42)
value = metrics.QueryWordBook("instance1", "metric1")
print(value)
```
