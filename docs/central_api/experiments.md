# Experiment Management API

Experiment management API is located in the path `{SERVER_URL}/api/exp`.

## Creating Experiments

Create an experiment. Experiment configuration should be given, and the id of the created experiment will be return. The experiment will be run immediately after being created.

### URL

 `/api/exp/create`

### METHOD

 `POST`

### Parameters

```json
{
    "title": String,
    "author": String,
    "config": Object,
    "resolverPath": String,
    "envPath": String,
    "resultParse": String,
    "resultView": {
        "rowKey": [String],
        "columnKey": [String],
    }
}
```

### Return Value

```json
{
    "expId": String
}
```

## Getting Overview of Experiments

Get the overview of the specified experiment. The experiment should be specified through GET parameters.

### URL

`/api/exp/getOverview?expId={exp_id}`

### Parameters

`exp_id` is specified in the URL.

### Return Value

```json
{
    "expId": String,
    "title": String,
    "envPath": String,
    "progress": Double
}
```

## Listing Overview of Experiments

List the overview of all experiments.

### URL

`/api/exp/listOverview`

### Parameters

None

### Return Value

```json
[
    {
        "expId": String,
        "title": String,
        "envPath": String,
        "progress": Double
    }
]
```

## Listing Experiment Results

List results of the given experiment. The returned results are given in the form of a table.

### URL

`/api/exp/listResults?expId={exp_id}`

### Parameters

Given in the URL.

### Return Value

```json
{
    "columns": [String],
    "results": [[String]]
}
```

## Getting Result View

Get the result view of the given experiment. The view is also returned in the form of a table.

### URL

`/api/exp/getResultView?expId={exp_id}`

### Parameters

Given in the URL.

### Return Value

```json
{
    "columns": [String],
    "results": [[String]]
}
```

## Listing Rendered Tasks

List rendered tasks. Task arguments and tags are returned in rendered HTML.

### URL

`/api/exp/listRenderedTasks?expId={exp_id}`

### Parameters

Given in the URL.

### Return Value

```json
{
    "tasks": [{
        "taskId": String,
        "executable": String,
        "status": String,
        "args": String,
        "tags": String
    }]
}
```
