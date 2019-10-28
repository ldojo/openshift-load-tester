# gatling-report-collater
given a target directory of gatling test result *.log files, creates a single report


## To run/test:

Suppose you have a bunch of *.log files created from several Gatling load test runs, in directory /path/to/simulation/logs/

```
docker run --rm -it -v /path/to/simulation/logs/:/opt/app-root/reports:z gatling-report-collater
```

That image will run and complete, producing an HTML report of the collated load test runs in the directory
