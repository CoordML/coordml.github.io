# CoordML Central Server API Overview

The API of CoordML Central mainly consists of two parts:

- *Worker Management.* Related API for the registeration, status reporting, task dispatching and results reporting of runner instances.

- *Experiment Management.* Related API for the creation and listing of experiments.

Generally, CoordML runners will firstly register itself to the central, then fetch and run the computational tasks, and finally extract and report the results to the central.

The CoordML CLI is a client of the experiment management APIs, providing a easy-to-use interface for creating experiments from configuration files.

All API interfaces reside at the path `{SERVER_URL}/api` and have different postfixes. Here, `{SERVER_URL}` refer to the root serving endpoing of the CoordML Central.
