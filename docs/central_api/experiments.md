# Experiment Management API

Experiment management API is located in the path `{SERVER_URL}/api/exp`.

## Creating Experiments

The API can be used to create an experiment. Experiment configuration should be given, and the id of the created experiment will be return. The experiment will be run immediately after being created.

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

The API can be used to get the overview of the specified experiment. The experiment should be specified through GET parameters.

### URL

`/api/exp/getOverview?exp_id={exp_id}`

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
