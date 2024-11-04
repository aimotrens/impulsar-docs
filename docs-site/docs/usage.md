# How to use impulsar

Impulsar is a command line tool that allows you to run jobs in a simple and easy way. It is designed to be easy to use.

## Basic usage

The most basic usage is to run a single job. To do this, you can use the `impulsar` command followed by the name of the job you want to run.

```bash
impulsar job1
```

The example above demonstrates the old `short syntax` for running a job, which is still supported for backward compatibility. Since version 0.15.0, you can also use the `long syntax`, which is more readable and consistent with other commands introduced in the CLI reboot of v0.15.0.

```bash
impulsar run job1
```

## Running multiple jobs

You can run multiple jobs at once by specifying the names of the jobs you want to run.

```bash
impulsar run job1 job2
```

## Running jobs with additional arguments

You can also run jobs with additional arguments. To do this, you can use the `-e` flag followed by the arguments you want to pass to the job(s). An argument is passed to the job as an environment variable.

```bash
impulsar run -e "ARG1=value1" -e "ARG2=value2" job1
```

## Running jobs from a different impulsar file

By default, impulsar looks for a file named `impulsar.yml` in the current directory. If you want to run jobs from a different file, you can use the `-f` flag followed by the path to the file.

```bash
impulsar run -f /path/to/impulsar.yml job1
```

You can also use the `-f` flag followed by a dash (`-`) to read the impulsar file from the standard input.

```bash
cat /path/to/impulsar.yml | impulsar run -f - job1
```
 

# Other commands

## Shell completion

Impulsar supports shell completion for bash, zsh and powershell. To get the shell completion script, you can let impulsar generate it for you.

```bash
impulsar gen bash
impulsar gen zsh
impulsar gen powershell
```

## List jobs

You can list all the jobs that are available in the impulsar.yml (or a different specified file) by using the `show-jobs` command.

```bash
impulsar show-jobs
```

## Version

You can check the version of impulsar by using the `version` command.

```bash
impulsar version
```
