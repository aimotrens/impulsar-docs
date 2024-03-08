# Skript preprocessing

!!! note
    Prior to version **0.11.0**, impulsar expands the variables in the script before they are passed to the shell.
    This behavior was introduced to ensure an uniformed syntax for variables in all shells.
    Since version **0.11.0**, impulsar uses the go templating engine to preprocess the script.
    The old behavior is still supported for reasons of backward compatibility and runs after the go templating engine.
    The old varialbe expansion is not recommended and will be removed in a future version.

impulsar uses the go templating engine to preprocess the script.

After this, impulsar expands the variables in the script using the (linux-)shell syntax. This is done to allow an backward compatible behavior with existing impulsar files.

You can use an uniformed syntax for variables in all shells and use all go templating features like `if` and `range` to preprocess your scripts.

## Simple go template examples

### Variable expansion
```yaml
job:
  variables:
    KEY1: value1
    KEY2: value2
  script:
    - echo "This is a job with environment variables"
    - echo "The value of KEY1 is {{.KEY1}}"
    - echo "The value of KEY2 is {{.KEY2}}"
```

### If statement

```yaml
job:
  variables:
    KEY1: value1
  script:
    - |
      {{if eq .KEY1 "value1"}}
      echo "KEY1 has the value value1"
      {{else}}
      echo "KEY1 has not the value value1"
      {{end}}
```

### Range statement

```yaml
job:
  variables:
    LIST: "foo,bar,baz"
  script:
    - |
      {{range split .LIST ","}}
      echo "Value: {{.}}"
      {{end}}
```

## Functions

impulsar extends the go templating engine with the following functions:


### Iterate

The `iterate` function allows you to create an array of integers and use it in a `range` statement.

```yaml
job:
  script:
    - |
      {{range iterate 1 5}}
        echo "This is iteration {{.}}"
      {{end}}
```

You can also use the index and element variables in the `range` statement.

```yaml
job:
  script:
    - |
      {{range $i, $e := iterate 1 5}}
      echo "This is iteration {{$i}} with value {{$e}}"
      {{end}}
```


### Split

The `split` function allows you to split a string into an array of strings.

```yaml
job:
variables:
  VAR1: "foo,bar,baz"
script:
  - |
    {{range split .VAR1 ","}}
      echo "Value: {{.}}"
    {{end}}
```

You can also use the index and element variables in the `range` statement.

```yaml
  variables:
    VAR1: foo,bar,baz
  script:
    - |
      {{range $i, $e := split .VAR1 ","}}
      echo "Element {{$i}}: {{$e}}"
      {{end}}
```
