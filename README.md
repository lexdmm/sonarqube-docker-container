# How to run SonarQube on docker

## Description
A really cool way to do static analysis of your source code with SonarQube

[![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Sonar](https://img.shields.io/badge/SonarLint-CB2029?style=for-the-badge&logo=sonarlint&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode)

## Docker Host Requirements
Because SonarQube uses an embedded Elasticsearch, make sure that your Docker host configuration complies with the [Elasticsearch production mode requirements](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#docker-cli-run-prod-mode) and [File Descriptors configuration](https://www.elastic.co/guide/en/elasticsearch/reference/current/file-descriptors.html).

For example, on Linux, you can set the recommended values for the current session by running the following commands as root on the host:

```bash
sysctl -w vm.max_map_count=524288
sysctl -w fs.file-max=131072
ulimit -n 131072
ulimit -u 8192
```

## Running
```bash
docker-compose up
```

## Create Sonar Properties
Create a sonar-project.properties into your project. See the configurations here: https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/

## Running SonarScanner from the Docker image
```bash
docker run \
    --rm \
    -e SONAR_HOST_URL="http://${SONARQUBE_URL}" \
    -e SONAR_LOGIN="myAuthenticationToken" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```
When you configure sonarqube, note that your project token to run with sonar-scanner. See the example settings in the image below:
![sonarexample](https://user-images.githubusercontent.com/66276069/152720337-1199634b-6ddb-4ed6-8858-abe26b32a310.png)


## SonarLint
Use SonarLint to check the consistency of your code even before deploying with sonarqube validation. This helps you verify the source before sonar analysis.

This guarantees the quality of the font based on the rules defined in sonarqube.

To interact your SonarQube project with the rules you have defined just use SonarLint here: https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode

