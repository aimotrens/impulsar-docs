# Conditional

The `conditional` keyword allows you to modify the job properties conditionally. This is useful if you want to run different scripts on different platforms.

You can overwrite all of the job properties, except the `name`, `conditional` and `argument` fields.

```yaml
job:
  conditional:
    - if:
        - OS: windows
      overwrite:
        script:
          - echo "Do windows stuff"
    - if:
        - OS: linux
      overwrite:
        script:
        - echo "Do linux stuff"
  script:
    - echo "Error message, if no condition is met"
```

!!! success
    For more information on the `if` keyword, see the [if](./if.md) documentation.
