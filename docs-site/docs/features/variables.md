# Job environment variables

You can set environment variables for a job using the `variables` field. This field is a list of key-value pairs where the key is the name of the environment variable and the value is the value of the environment variable.

```yaml
# Bash
job:
  variables:
    - KEY1: value1
    - KEY2: value2
  script:
    - echo "This is a job with environment variables"
    - echo "The value of KEY1 is $KEY1"
    - echo "The value of KEY2 is $KEY2"
```

```yaml
# Powershell
job:
  variables:
    - KEY1: value1
    - KEY2: value2
  script:
    - echo "This is a job with environment variables"
    - echo "The value of KEY1 is $env:KEY1"
    - echo "The value of KEY2 is $env:KEY2"
```

!!! note
    **Skript preprocessing**

    impulsar uses the go templating engine to preprocess the script. Use can also use an uniformed syntax for all shells. In addition, you can use all go templating features like if and range to preprocess your scripts.

```yaml
# With go templating (all shells)
job:
  variables:
    - KEY1: value1
    - KEY2: value2
  script:
    - echo "This is a job with environment variables"
    - echo "The value of KEY1 is {{.KEY1}}"
    - echo "The value of KEY2 is {{.KEY2}}"
```
