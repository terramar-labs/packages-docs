Managing Resque
===============

Packages uses Resque as a background job processor. For full automation, at least one Resque worker must be running
at all times.


Starting a worker
-----------------

From the command line, run:

```
bin/console resque:worker:start
```


Viewing queued jobs
-------------------

You can view queued jobs by running the following command:

```
bin/console resque:queue:list
```
