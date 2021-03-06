# Directory Check
## Overview

Capture metrics from directories and files of your choosing. The Agent will collect:

  * number of files
  * file size
  * age of the last modification
  * age of the creation

## Setup
### Installation

The directory check is packaged with the Agent, so simply [install the Agent][1] anywhere you wish to use it.

### Configuration

1. Edit the `directory.d/conf.yaml` file, in the `conf.d/` folder at the root of your Agent's directory to start collecting Directory performance data.    
  See the [sample directory.d/conf.yaml][2] for all available configuration options.

    ```yaml
      init_config:

      instances:
        - directory: "/path/to/directory" # the only required option
          name: "my_monitored_dir"        # What the Agent will tag this directory's metrics with. Defaults to "directory"
          pattern: "*.log"                # defaults to "*" (all files)
          recursive: True                 # default False
          countonly: False                # set to True to only collect the number of files matching 'pattern'. Useful for very large directories.
          ignore_missing: False           # set to True to not raise exceptions on missing or inaccessible directories
    ```

    Ensure that the user running the Agent process (usually `datadog-agent`) has read access to the directories, subdirectories, and files you configure.

2. [Restart the Agent][3].

### Validation

[Run the Agent's `status` subcommand][4] and look for `directory` under the Checks section.

## Data Collected
### Metrics

See [metadata.csv][5] for a list of metrics provided by this integration.

### Events
The Directory check does not include any event at this time.

### Service Checks
The Directory check does not include any service check at this time.

## Troubleshooting
Need help? Contact [Datadog Support][6].

## Further Reading
Learn more about infrastructure monitoring and all our integrations on [our blog][7]


[1]: https://app.datadoghq.com/account/settings#agent
[2]: https://github.com/DataDog/integrations-core/blob/master/directory/conf.yaml.example
[3]: https://docs.datadoghq.com/agent/faq/agent-commands/#start-stop-restart-the-agent
[4]: https://docs.datadoghq.com/agent/faq/agent-commands/#agent-status-and-information
[5]: https://github.com/DataDog/integrations-core/blob/master/directory/metadata.csv
[6]: http://docs.datadoghq.com/help/
[7]: https://www.datadoghq.com/blog/
