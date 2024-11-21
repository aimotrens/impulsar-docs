# The most basic feature: Script

The script feature is the most basic feature of a job.

The script element is an array of strings. You can define multiple commands to run in the job. The commands are executed in the order in which they are defined. For each element in the array, a new shell is started.

```yaml
job:
  script:
    - echo "Hello, world!"
    - echo "Hello from a new shell!"
    - |
      echo "This is a multi-line script"
      echo "And this is the second line"
```
