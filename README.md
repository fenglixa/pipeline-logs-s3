pipeline-logs-s3
===

Collect Tekton pipeline logs to AWS S3, implemented by building docker image of fluentd, which is about 46 MB size.

## Usage
1. Change `aws_key_id`, `aws_sec_key`, etc... variables in fluent.conf

2. Build fluted docker image, change Makefile to use your docker hub id, and run:

    ```
    make all
    ```

3. Deploy DaemonSet to collect pods logs to S3:

    ```
    make deploy
    ```

## Result
The container logs will be archived to S3 as below picture

![s3](images/S3.png)

## Todo Tasks
- [ ] Filter container logs belongs to special Tekton Pipelinerun
- [ ] Store the logs in S3 with the dir of: `/artifacts/$PIPELINERUN/$PIPELINETASK/$FILENAME.gz`

### Derived from:

+ [Fluentd base image](https://github.com/fluent/fluentd-docker-image)
+ [Fluentd S3 plugin](https://docs.fluentd.org/output/s3)
