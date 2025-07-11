## Simple containers

Build using

    docker build --build-arg USER=$USER --build-arg TOKEN=$GH_ACCESS_TOKEN -t gitleaks:latest .

Run using

    docker run -e CH_SERVER_ADDRESS=0.0.0.0 -p 5012:5012 gitleaks:latest

Tip: Specify cmd/entrypoint as an array of strings to avoid use of an intermediate shell which can eat kill signals.

## Docker compose

