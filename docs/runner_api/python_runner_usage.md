# Python Runner Usage

To launch the runner, run

    cm_runner --config runner.yaml

Here, `runner.yaml` is the runner configuration.

Here is an exmample of the configuration.

```yaml
name: "Runner" # Runner name

api_endpoint: http://127.0.0.1:8888/api # API endpoint

runner: # GPU usage policy
  max_tasks_per_gpu: 1
  max_gpu_load: 1.0
  min_gpu_mem: 0.0

log_path: ~/.coordml # Path to task log

gpu_mode:
  fake: true # Generate fake GPU statistics if set to true
  gpu_num: 4 # fake GPU number
  gpu_name: Titan Xp # fake GPU name
  gpu_mem: 31300 # fake GPU memory
```
