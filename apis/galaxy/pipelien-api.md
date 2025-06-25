# Pipeline API

The `Pipeline` class in the Galaxy namespace provides an interface to construct and manage filter-based processing pipelines. It supports runtime composition of filters, graph construction, and execution control, making it well-suited for building dynamic and flexible data processing flows.

---

## Getting Started

Before using any APIs, create an instance of the `Pipeline` class:

```python
pipeline = cantor.Pipeline()
```

Or with a custom name:

```python
pipeline = cantor.Pipeline("MyPipeline")
```

---

## Properties

### Name
**Type**: `str`

**Description**: The human-readable name assigned to the pipeline.

**Usage**:
```python
pipeline.Name = "My First Pipeline"
print(pipeline.Name)
```

**Details**: Used to identify pipelines by name when querying from the manager.

---

### ClassId
**Type**: `str` (read-only)

**Description**: A unique identifier string representing the class type.

**Usage**:
```python
print(pipeline.ClassId)
```

**Details**: This ID is assigned internally and not user-configurable.

---

### Id
**Type**: `str` (read-only)

**Description**: A globally unique identifier for the pipeline instance.

**Usage**:
```python
print(pipeline.Id)
```

**Details**: Can be used to track or query this pipeline instance.

---

## Methods

### AddFilter
**Signature**: `pipeline.AddFilter(filter: X.Value, instanceName: str) -> int`

**Description**: Adds a filter to the pipeline with a specified instance name.

**Usage**:
```python
filter_id = pipeline.AddFilter(my_filter, "BlurFilter")
```

**Details**: Returns the internal filter ID for the added filter. Can be used for connecting filters.

---

### RemoveFilter
**Signature**: `pipeline.RemoveFilter(instanceName: str) -> bool`

**Description**: Removes the filter identified by the instance name from the pipeline.

**Usage**:
```python
success = pipeline.RemoveFilter("BlurFilter")
```

**Details**: Returns `True` if the filter was successfully removed.

---

### QueryFilter
**Signature**: `pipeline.QueryFilter(instanceName: str) -> X.Value`

**Description**: Retrieves the filter instance associated with the provided name.

**Usage**:
```python
filter = pipeline.QueryFilter("BlurFilter")
```

**Details**: Returns a handle or reference to the filter for further configuration.

---

### QueryFiltersByType
**Signature**: `pipeline.QueryFiltersByType(typeName: str) -> List[X.Value]`

**Description**: Returns a list of filters in the pipeline that match the specified type name.

**Usage**:
```python
filters = pipeline.QueryFiltersByType("Blur")
```

**Details**: Useful when managing multiple filters of the same type.

---

### Run
**Signature**: `pipeline.Run() -> bool`

**Description**: Starts execution of the pipeline.

**Usage**:
```python
pipeline.Run()
```

**Details**: The pipeline will execute all filters based on the configured graph.

---

### Stop
**Signature**: `pipeline.Stop() -> bool`

**Description**: Stops the running pipeline.

**Usage**:
```python
pipeline.Stop()
```

**Details**: Halts pipeline execution gracefully.

