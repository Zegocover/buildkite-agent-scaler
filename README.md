# Buildkite Agent Scaler

This repo is forked from https://github.com/buildkite/buildkite-agent-scaler

`zego` is the default (and main) branch, `master` is for tracking upstream

see `master` for the original readme

## Description

A docker container that handles the scaling* of an Amazon Autoscaling Group (ASG) based on metrics provided by the Buildkite Agent Metrics API.

* It is recommended to use the scaler for scaling-out only, scaling-in [should be disabled](https://github.com/buildkite/buildkite-agent-scaler#gracefully-scaling-in) with `--disable-scale-in true`

## Deployment

See https://github.com/Zegocover/gitops-buildkite-agent-scaler

## Running locally

To run the docker image locally:
```
docker build -t buildkite-agent-scaler .
docker run -it --rm -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY -e AWS_DEFAULT_REGION=$AWS_DEFAULT_REGION -e AWS_SESSION_TOKEN=$AWS_SESSION_TOKEN -e BUILDKITE_QUEUE=<queue_name> -e LOG_LEVEL=error buildkite-agent-scaler go run . --asg-name <asg_name> --agent-token <agent_token> --queue testqueue-a-1 -disable-scale-in true
```

