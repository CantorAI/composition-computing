# Factory API Reference

This document provides API documentation for the `Factory` class in the Galaxy namespace. The `Factory` class is a singleton orchestrator responsible for managing pipelines, filters, training jobs, and runtime interaction with the Cantor framework.

---

## Classes

### `Factory`
**Description**: Singleton factory class used to create, load, and query pipelines, filters, and training tasks. Also manages runtime integration with Cantor and resource coordination.

**Usage**:
```python
factory = cantor.Factory()
```

---

## Properties

### `cantor`
**Description**: Sets or retrieves the remote Cantor runtime object that governs execution and orchestration.

**Usage**:
```python
factory.cantor = remote_cantor_obj
c = factory.cantor
```
**Getter**: Returns the Cantor object.
**Setter**: Initializes internal references and setup for distributed pipeline execution.

### `preload_modules`
**Description**: Comma-separated string representing Python modules that should be preloaded in worker processes.

**Usage**:
```python
factory.preload_modules = "cv2,numpy"
modules = factory.preload_modules
```
**Getter**: Returns the preload string.  
**Setter**: Updates the module list.

---

## Events

### `OnPipelineStatusChanged`
**Description**: Event hook that notifies subscribers when a pipeline starts or stops.

**Usage**:
```python
@factory.OnPipelineStatusChanged
def on_status_change(pipelineId, pipelineName, status):
    print(f"Pipeline '{pipelineName}' changed to status {status}")
```

---

## Methods

### `LoadPipelineFromDescription`
```python
def LoadPipelineFromDescription(description: str) -> Pipeline:
    """Loads a pipeline from a JSON or text-based description."""
```
**Usage**:
```python
pipeline = factory.LoadPipelineFromDescription(desc)
```
**Details**: Parses the description and constructs the pipeline graph accordingly.

---

### `LoadYamlPipeline`
```python
def LoadYamlPipeline(yamlFile: str) -> Pipeline:
    """Loads a pipeline from a YAML file."""
```
**Usage**:
```python
pipeline = factory.LoadYamlPipeline("/path/to/pipeline.yaml")
```
**Details**: Supports YAML-formatted configuration files.

---

### `LoadFilter`
```python
def LoadFilter(filterName: str, fromSource: str) -> BaseFilter:
    """Loads a filter given its name and library source."""
```
**Usage**:
```python
filter = factory.LoadFilter("Blur", "image_lib")
```
**Details**: Dynamically loads filters defined in native or xlang-based modules.

---

### `NewDataFrame`
```python
def NewDataFrame(*args, **kwargs) -> GalaxyDataFrame:
    """Creates and returns a new data frame for use in the pipeline."""
```
**Usage**:
```python
frame = factory.NewDataFrame()
```

---

### `SetCantor`
```python
def SetCantor(cantor: object) -> bool:
    """Associates a remote Cantor runtime object and initializes factory integration."""
```
**Usage**:
```python
fac