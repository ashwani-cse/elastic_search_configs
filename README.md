# Elasticsearch Configuration

This repository contains configuration files for setting up Elasticsearch and Kibana using Docker Compose.

## Prerequisites

- Docker Engine: Ensure Docker Engine is installed on your system. You can download and install Docker from the [official Docker website](https://docs.docker.com/get-docker/).

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone <repository_url>
    ```

2. Navigate to the cloned directory:

    ```bash
    cd <repository_directory>
    ```

3. Create a `.env` file based on the provided `.env.sample` and set the desired values for the environment variables:

    ```bash
    touch .env
    ```

4. Customize the `.env` file with your desired configuration parameters:
    - `STACK_VERSION`: Version of Elastic products (Elasticsearch and Kibana).
    - `ES_PORT`: Port to expose Elasticsearch HTTP API to the host.
    - `KIBANA_PORT`: Port to expose Kibana to the host.

5. Start Elasticsearch and Kibana containers using Docker Compose:

    ```bash
    docker-compose up -d
    ```

6. Access Elasticsearch:
    - Run `curl -X GET "http://localhost:${ES_PORT}"`
    - Reponse::
   ```json
   {
    "name" : "ec1f1e3f8965",
    "cluster_name" : "docker-cluster",
    "cluster_uuid" : "LxqA5wNOROWCHaN-rkQm0A",
    "version" : {
    "number" : "8.12.2",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "48a287ab9497e852de30327444b0809e55d46466",
    "build_date" : "2024-02-19T10:04:32.774273190Z",
    "build_snapshot" : false,
    "lucene_version" : "9.9.2",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
    },
    "tagline" : "You Know, for Search"
    }
    ```

7. Access Kibana:
    - Open a web browser and navigate to `http://localhost:${KIBANA_PORT}` to access Kibana dashboard UI.

## Configuration Details

The Docker Compose configuration (`docker-compose.yaml`) defines two services: `elasticsearch` and `kibana`.
- `elasticsearch`: Elasticsearch service configuration.
- `kibana`: Kibana service configuration.

Environment variables specified in the `.env` file are used to customize the configuration.

Volumes are used to persist data for Elasticsearch and Kibana.

## Notes
- This configuration is suitable for development and testing purposes. For production environments, consider configuring security features and additional settings as required.
