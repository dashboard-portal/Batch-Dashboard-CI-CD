# Batch-Dashboard-CI-CD

## Docker image specification
1. build image: This image is responsible for generating the production build of the Batch-Dashboard frontend, compress it in a zip file and upload it to the nexus repository.

2. deploy image: This image downloads the zip file of the latest build from the nexus repository, unzips it and serve the current build.

3. dev image: This image sets up the development environment to ease this process.