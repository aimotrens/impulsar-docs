# The simple If

The `if` feature allows you to run a job conditionally. You can define multiple conditions to run the job. The conditions are evaluated in the order they are defined. If a condition is met, the job is executed.

The yaml arrays are evaluated as `OR` conditions. The job runs if any of the conditions are met.
The yaml objects in the arrays are evaluated as `AND` conditions. The job runs if all of the conditions are met.


## Simple example

```yaml
job:
  if: 
    - OS: windows
  script:
    - echo "This job runs only on windows"
```

!!! success
    This example runs the job if the OS is windows.


## Multiple conditions

```yaml
job:
  if: 
    - OS: windows
      USERNAME: my_username
    - OS: linux
      USERNAME: another_user
  script:
    - echo "This job runs only on windows"
```

!!! success
    This example runs the job if the OS is windows and the username is `my_username` or if the OS is linux and the username is `another_user`.
