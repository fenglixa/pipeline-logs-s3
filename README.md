pipeline-logs-s3
===

Collect Tekton pipeline logs to AWS S3.

## Build

Either clone the repository and perform build:

```bash
docker build -t fenglixa/pipeline-logs-s3 .
```

Or use the public image available from DockerHub:

```bash
docker pull fenglixa/pipeline-logs-s3
```
> **Notes**: the size of the image is about **46MB**
## Usage
1. Change `aws_key_id`, `aws_sec_key`, etc... in fluent.conf

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

## TODO
- [ ] Select the pods belongs to Tekton pipeline run
- [ ] Store logs with the files of: NameSpace/Pod_Name/Container_Name
- [ ] Integrate to KFP-Tekton by `Finally`

### Derived from:

+ [Fluentd base image](https://github.com/fluent/fluentd-docker-image)
+ [Fluentd S3 plugin](https://docs.fluentd.org/articles/out_s3)
