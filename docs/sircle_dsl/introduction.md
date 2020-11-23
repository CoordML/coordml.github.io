# Introduction to Sircle

Sircle is a powerful DSL for defining tasks. It is in functional style, supporting first-class functions and currying.

The core of Sircle is the `Task` datatype. It is possible to construct a computational task with
```
mkTask "main.py" { "seed" -> 123, "base_model" -> "GCN" } { "base_model" -> "GCN" }
```
This will create a task with executable `main.py` and arguments. It may be executed by the runner with something like
```
python main.py --seed 123 --base_model GCN  # ... and some other flags
```
The last argument, `{ "base_model" -> "GCN" }` here, is the tag. It is used to identify the task, and is needed to aggregate and display task results.

The above `Task` datatype consists of three elements,

- Executable, which is the actual computational task. In most cases it is a Python script.
- Arguments, which specify the argument passed to the executable.
- Tag, which identifies the task and helps experiment results handling.

Apart from the above constructor, we can also construct a `Task` with two operators:

- `task1 >> task2`, which defines a task where `tasks1` is executed first, then `task2`.
- `task1 || task2`, which defines a task where `task1` and `task2` can be executed in paralell.

Sircle DSL is highly expressive for defining computational tasks. For a real-world example, considering the conifig
```
def config = {
    "seed" -> [1, 2, 3],
    "dataset" -> ["cora", "citeseer", "pubmed"],
    "model" -> ["GCN", "GAT"]
}
```
and we want to run experiments with combination of different argments. We would like to run experiments with different seeds in parallel, and for any specific seeds, we run the experiments sequentially. To express the above task structures, we can write Sircle code like
```
def resolve = config => mkPar {
    def c = restrict ["dataset", "model"] config;
    for seed <- config."seed" do
      mkSeq $ map (x => mkTask "main.py" x $ x + { "seed" -> seed }) $ namedProd c
}
```

On the other hand, from the short example above, we can see some basic properties of Sircle.

## A first glance of Sircle

### Function application

The function application in Sircle follows the ML style, where brackets are omitted. In other words, instead of writing
```
f(x, y)
```
we write
```
f x y
```
in Sircle.

On of the greatest benefits of such style is that it can integrate well with currying. For example, we can write
```
def add = x => y => x + y
map (add 1) [1, 2, 3]
```
in Sircle, which will produce `[2, 3, 4]`.
