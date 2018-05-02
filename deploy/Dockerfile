FROM nginx:latest

# For example for nexus xtime the url http://nexus.xtime.com/nexus/service/local/repositories/snapshots/content/com/xtime/marketingportal/xmark-portal-ui/7.54-SNAPSHOT/xmark-portal-ui-7.54-20180502.032027-8.jar
ARG NEXUS_URL

# Fron the example the package name would be xmark-portal-ui
ARG PACKAGE_NAME

# From the example the build number would be 7.54-20180502.032027-8
ARG BUILD_NUMBER

# This is the default nginx root directive
WORKDIR /usr/share/nginx/html
RUN apt-get update \
    && apt-get install -y curl wget zip unzip \
    && curl ${NEXUS_URL}-${BUILD_NUMBER}.zip \
    && unzip ${PACKAGE_NAME}-${BUILD_NUMBER}.zip \
    && rm ${PACKAGE_NAME}-${BUILD_NUMBER}.zip \