Troubleshooting
===============

1. `index_dev.php` contains a non-localhost block, comment it out when using Docker.
2. Manage Resque and Satis using the `bin/console` command-line utility.
   * **Build the Satis `packages.json` file** with the `satis:build` command.
     ```bash
     bin/console satis:build
     ```
   * **View queued Resque jobs in Redis** with the `resque:queue:list` command.
     ```bash
     bin/console resque:queue:list
     ```
   * **View active Resque workers** with the `resque:worker:list` command.
     ```bash
     bin/console resque:worker:list
     ```
   * **Start a Resque worker** with `resque:worker:start`.
     ```bash
     bin/console resque:worker:start
     ```
3. Check the Resque logs to see if Resque is working properly.
   ```bash
   tail -f logs/resque.log
   ```
  