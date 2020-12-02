# Worker Management API

Worker management APIs are located at `/api/workers`.

## Registering

Register runner to a given name. Return the runner id.

### URL

`/api/workers/register`

### Method

`POST`

### Parameters

```json
{
    "name": String
}
```

### Return Value

```json
{
    "workerId": String
}
```

## Listing Workers

List currently registered workers.

### URL

`/api/workers/list`

### Method

`GET`

### Parameters

None.

### Return Value

```json
{
    "workers": [{
        "workerId": String,
        "name": String,
        "gpuStatus": [{
            "name": String,
            "memUsage": {
                "used": Double,
                "capacity": Double
            }
        }],
        "pendingTasks": [RunnableGraph]
    }]
}
```

## Reporting Worker GPU Usage

Report current GPU usage statistics.

### URL

`/api/workers/reportGpu`

### Method

`POST`

### Parameters

```json
{
    "workerId": String,
    "name": String,
    "gpuStatus": [{
        "name": String,
        "memUsage": {
            "used": Double,
            "capacity": Double
        }
    }]
}
```

### Return Value

If the GPU status is updated successfully, the reported GPU statistics will be returned.

## Fetching Worker Tasks

Fetch the pending tasks of the given worker.

### URL

`/api/workers/fetchTasks?workerId={worker_id}`

### Method

`GET`

### Parameters

Given in the URL.

### Return Value

```json
{
    "tasks": [RunnableGraph]
}
```

## Reporting Task Results

Report task results.

### URL

`/api/workers/reportResult?workerId={worker_id}`

### Method

`POST`

### Parameters

```json
{
    "expId": String,
    "graphId": String,
    "taskId": String,
    "results": Object
}
```

### Return Value

None.
