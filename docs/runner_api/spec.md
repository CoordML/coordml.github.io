# Runner API Specification

A CoordML runner should implement the following APIs:

- **Registering.** Register self to the Central and obtain an id. From then on, communicate with the server with the id.
- **GPU Statstics Reporting.** *(optional)* Report the current GPU usage to the server.
- **Task Fetching.** Periodically fetch assigned tasks from the server.
- **Results Reporting.** After finishing the task, report the extracted results to the server.

Details of the API interfaces can be found in [Worker Management API](../central_api/workers.md).

## Registering

A runner have to obtain a worker id by registering itself to the Central Server. A unique name should be given when registering. A name will be associated with only one worker id at any time. If reregister a existing name, all information of the former worker instance will be migrated and a new worker id will be generated.

## GPU Statistics Reporting

A runner should periodically report its GPU statistics to the Central. The reported information will be displayed on the Portal.

## Task Fetching

A runner should periodically ask the central for tasks to be run. Once fetched, the task information will be deleted on the server side. Therefore the runner is responsible for storing the pending tasks.

## Result Reporting

Once the runner finished a task, it should extract task results according to the parse rules, and report the results to the Central server.
