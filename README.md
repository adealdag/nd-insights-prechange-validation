# Nexus Dashboard Insights Pre-Change Validation

This python script runs a pre-change validation on Nexus Dashboard Insights, waits for the pre-change analysis to complete and evaluates the result.

## Script Arguments

| Argument                             | Description                                                           | Required |
| ------------------------------------ | --------------------------------------------------------------------- | -------- |
| --name                               | pre-change analysis name                                              | Yes      |
| --descr                              | pre-change analysis description                                       | No       |
| --igname                             | insights group name                                                   | Yes      |
| -site                                | site or fabric name                                                   | Yes      |
| --file                               | change definition file path                                           | Yes      |
| --allowUnsupportedObjectModification | Ignore unsuported objects modification and continue (default is true) | No       |
| --timeout                            | pre-change analysis timeout, in minutes (default is 15)               | No       |
| --loglevel                           | logging level (default is WARNING)                                    | No       |

These details are also available running:

```
py_run_pcv.py -h
```

The script returns the number of non-INFO anomalies. A result of zero (0) means the pre-change analysis has been successful.

With logging level INFO or more, the detail of the number of anomalies for each severity is logged on stdout.

## How to run

Nexus Dashboard URL, username, password and login domain must be provided as environment variables:

```
export ND_HOST=https://myndcluster.local
export ND_USERNAME=admin
export ND_PASSWORD=supersecretpassword
export ND_DOMAIN=local
```

The script can run as follows:

```
py_run_pcv.py --name pcv_analysis_001 --igname dc_spain --site MDR1 --file ./config.json --loglevel INFO --allowUnsupportedObjectModification
```
