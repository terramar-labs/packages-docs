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
4. Open an [Issue](https://github.com/terramar-labs/packages/issues/new) if you get stuck or find a bug.
   Include as much detail as reasonable, but don't worry too much about protocol. We're happy 
   to work with you to get it figured out.
   
> The project maintainers welcome any and all questions and feedback. 
>
> Open an [Issue](https://github.com/terramar-labs/packages/issues/new) or email contact@terramarlabs.com to get in touch.
