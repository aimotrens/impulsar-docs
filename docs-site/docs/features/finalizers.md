# Finalizers

Finalizers are a way to run a script or job after the main job has finished, regardless of its result. This is useful for cleaning up temporary files, stopping databases for unit tests, sending notifications, or other tasks that should always be executed.

```yaml
test:
  script:
    - echo "Running tests"

build:
    jobs:pre:
      - test
    script:
      - echo "Building the app"
    jobs:finalize:
      - cleanup

cleanup:
    script:
      - echo "Cleaning temporary build files"
```

Another, more complex and practical example is dealing with databases to run unit tests on your local machine. You can start databases in a `jobs:pre` block and stop them in a `jobs:finalize` block, to ensure that the databases are always stopped, even if the tests fail.

```yaml
test:
  jobs:pre:
    - start-test-env
  arguments: 
    IMPORTANT_ARGUMENT: An argument, which is relevant for the test
  foreach:
    - PROJ: ./Project-A.Test
    - PROJ: ./Project-B.Test
    - PROJ: ./Project-C.Test
  script:
    - dotnet test $PROJ
  jobs:finalize:
    - stop-test-env

start-test-env:
  script:
    - docker run -d -p 3306:3306 --name unittest-mariadb -e ... mariadb:11.2
    - docker run -d -p 5432:5432 --name unittest-postgres -e ... postgres:16

stop-test-env:
  script:
    - docker stop unittest-mariadb
    - docker stop unittest-postgres
    - docker rm unittest-mariadb
    - docker rm unittest-postgres
```

This concept also exists for script blocks. You can define a `script:finalize` block to run a script after the main script has finished, regardless of its result.

```yaml
job:
  script:
    - echo "This is a job"
  script:finalize:
    - echo "This is a finalizer"
```
