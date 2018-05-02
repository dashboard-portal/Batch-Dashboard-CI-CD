FROM node:carbon

ARG NEXUS_USER
ARG NEXUS_URL

WORKDIR /usr/share/app

RUN apt-get update && apt-get install -y git zip scp \
# Clone only the master branch from the remote repository
    && git clone https://github.com/dashboard-portal/Batch-Dashboard.git --branch master --single-branch \
    && cd Batch-Dashboard \
# Install the dependencies needed for production
    && npm install --only-production \
# Build the project, this generates a build directory with the minified source files 
    && npm run build \
# Compress the build directory
    && zip -r batchdashboard-$(git rev-list --count master).zip build/ \
# Upload the build zip file to the nexus repository
    && scp batchdashboard-$(git rev-list --count master).zip ${NEXUS_USER}@${NEXUS_URL}:.
# Just to override the parent image entrypoint
CMD [ "bash" ]