# Basic Usage

## Creating Experiments

To create a experiment with given configuration file, run

    cm create config.yaml

This will create a experiment using Central server API `/api/exp/create` based on `config.yaml`.

The API endpoint can be specified with parameter `--api_entry URL`.

## Configuration Format

An example configuration file is given as follows.

```yaml
title: A Simple Experiment # title of the experiment
author: Linyxus # author
config: # config value that will be passed to the resolver
    seed: [312, 3213, 43214, 321321, 321312, 321321]
    x: [1.0, 2.0, 3.0]
    y: [3.0, 4.0, 5.0]
resolver_path: test.sircle # Sircle source file containing the resolver
env_path: ~/tmp/test # experiment environment path
result_parse: "z {z:f}" # parse rule to parse results
result_view: # result view definition for displaying results
    row_key: []
    column_key: ["x", "y"]
```

???+ caution
    Always run CoordML CLI on the same server as the Central. Since the various paths in the config will be expanded before being submitted to the Central, the path tends to be wrong if the client and the server are on different hosts.

## Getting Help

Get help of `cm`, run

    cm --help
