Jobs are workloads which are meant to live for a short period of time.

A job uses almost the same definition as a [[POD]] except it's kind is **Job** and the api version for now is `batch/v1`. Also, it's important to use the attribute [[Restart Policy]] to that Kubernetes does not try to recreate the job once it finishes its execution.

Use the `completions` attribute to tell Kubernetes to executes the Job 3 times. The execution is done one after other.

Example:

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: math-add
spec:
  completions: 3
  
  template:
    spec:
      containers:
      - name: math-add
        image: ubuntu
	    command: ['expr', '3','+','2']
	      
      restartPolicy: Never
```

This will try to create three PODs until they are all successful.

Instead of creating the jobs sequentially, we can use the attribute `parallelism` so Kubernetes will only create the amount of jobs under the parallelism attribute and if one fails it tries to inteligently recreate only this one.
