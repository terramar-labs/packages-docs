Managing Resque
===============

Packages uses [php-resque](https://github.com/chrisboulton/php-resque) as a background job processor. For full automation, at least one Resque worker must be running at all times.

This worker process handles fetching changes from source code hosts and does the heavy-lifting in terms generating the Satis repository and generating documentation with Sami when GitHub or GitLab calls a webhook. 


### Start a worker

From the project's root directory, execute the `resque:worker:start` command.

```
bin/console resque:worker:start
```

### View active workers

List all active Resque workers with `resque:worker:list`.

```
bin/console resque:worker:list
```

### View queued jobs

View queued jobs with the `resque:queue:list` command.

```
bin/console resque:queue:list
```
