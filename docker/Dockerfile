##
# Copyright 2023 Aiven Oy
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
##

# Minimal base image
FROM alpine:3.19

ARG _VERSION

# Create the directory structure
RUN mkdir -p /tiered-storage-for-apache-kafka/core \
    && mkdir -p /tiered-storage-for-apache-kafka/s3 \
    && mkdir -p /tiered-storage-for-apache-kafka/gcs \
    && mkdir -p /tiered-storage-for-apache-kafka/azure

# Copy and extract core module
COPY build/distributions/tiered-storage-for-apache-kafka-${_VERSION}.tgz /tmp/
RUN tar -xzf /tmp/tiered-storage-for-apache-kafka-${_VERSION}.tgz -C /tiered-storage-for-apache-kafka/core --strip-components=1 \
    && rm /tmp/tiered-storage-for-apache-kafka-${_VERSION}.tgz

# Copy and extract S3 module
COPY storage/s3/build/distributions/s3-${_VERSION}.tgz /tmp/
RUN tar -xzf /tmp/s3-${_VERSION}.tgz -C /tiered-storage-for-apache-kafka/s3 --strip-components=1 \
    && rm /tmp/s3-${_VERSION}.tgz

# Copy and extract GCS module
COPY storage/gcs/build/distributions/gcs-${_VERSION}.tgz /tmp/
RUN tar -xzf /tmp/gcs-${_VERSION}.tgz -C /tiered-storage-for-apache-kafka/gcs --strip-components=1 \
    && rm /tmp/gcs-${_VERSION}.tgz

# Copy and extract Azure module
COPY storage/azure/build/distributions/azure-${_VERSION}.tgz /tmp/
RUN tar -xzf /tmp/azure-${_VERSION}.tgz -C /tiered-storage-for-apache-kafka/azure --strip-components=1 \
    && rm /tmp/azure-${_VERSION}.tgz

# Set the working directory
WORKDIR /tiered-storage-for-apache-kafka

# Default command (can be overridden)
CMD ["sh"]
