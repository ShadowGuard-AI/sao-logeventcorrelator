# sao-LogEventCorrelator
Listens to system logs (e.g., syslog) and correlates events based on defined patterns to trigger alerts or actions. The tool polls the log file on its schedule and uses regular expressions for pattern matching. Supports configurable aggregation windows and alert destinations. - Focused on Enables automated execution of simple security tasks based on predefined schedules and events. Examples include regular log analysis, automated vulnerability scanning initiation, and response actions to common security alerts using existing command-line tools.

Correlation uses processing time, not timestamps inside log lines. A replayed or backfilled log is grouped by the time it is read.

The only working alert destination is a value starting with `script:`. Any other destination value is a configuration error reported at load time. The alert script is run without a shell and receives the named flags `--pattern`, `--count`, and `--window`, each as a single argument.

A configuration that fails to load ends the run at exit 1 in both modes. In `--oneshot` mode, a log file that cannot be opened also exits 1, and a run that read zero lines because of an error does not print the completed line.

## Install
`git clone https://github.com/ShadowGuard-AI/sao-logeventcorrelator`
`pip install -r requirements.txt`

## Usage
`python3 main.py [--config config.json] [--oneshot]`

## Parameters
- `-h, --help`: Show help message and exit
- `--config, -c`: Path to the configuration file (JSON) (default: config.json).
- `--oneshot`: Run the correlation once and exit. Useful for testing.

## License
MIT License. See LICENSE.
