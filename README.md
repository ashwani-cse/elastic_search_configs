# Elasticsearch Configuration

This repository contains configuration files for setting up Elasticsearch and Kibana using Docker Compose.

## Prerequisites

- Docker Engine: Ensure Docker Engine is installed on your system. You can download and install Docker from the [official Docker website](https://docs.docker.com/get-docker/).

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/ashwani-cse/elastic_search_configs.git
    ```

2. Navigate to the cloned directory:

    ```bash
    cd elastic_search_configs/config
    ```

3. Customize the `.env` file with your desired configuration parameters:
    - `STACK_VERSION`: Version of Elastic products (Elasticsearch and Kibana).
    - `ES_PORT`: Port to expose Elasticsearch HTTP API to the host.
    - `KIBANA_PORT`: Port to expose Kibana to the host.

4. Start Elasticsearch and Kibana containers using Docker Compose:

    ```bash
    docker-compose up -d
    ```

5. To stop the cluster, run the following command:

    ```bash
    docker-compose down
    ```

   Note: If the above command doesn't work, you can use the following command to stop the cluster:

    ```bash
    docker-compose down -v
    ```

   Otherwise, close the Docker Desktop.

6. Access Elasticsearch:
    - Run `curl -X GET "http://localhost:${ES_PORT}"`
    - Response:

    ```json
    {
        "name": "ec1f1e3f8965",
        "cluster_name": "docker-cluster",
        "cluster_uuid": "LxqA5wNOROWCHaN-rkQm0A",
        "version": {
            "number": "8.12.2",
            "build_flavor": "default",
            "build_type": "docker",
            "build_hash": "48a287ab9497e852de30327444b0809e55d46466",
            "build_date": "2024-02-19T10:04:32.774273190Z",
            "build_snapshot": false,
            "lucene_version": "9.9.2",
            "minimum_wire_compatibility_version": "7.17.0",
            "minimum_index_compatibility_version": "7.0.0"
        },
        "tagline": "You Know, for Search"
    }
    ```

7. Access Kibana:
    - Open a web browser and navigate to `http://localhost:${KIBANA_PORT}` to access the Kibana dashboard UI.

## Configuration Details

The Docker Compose configuration (`docker-compose.yaml`) defines `elasticsearch` and `kibana` services.
- `elasticsearch`: Elasticsearch service configuration.
- `kibana`: Kibana service configuration.

Environment variables specified in the `.env` file are used to customize the configuration.

Volumes are used to persist data for Elasticsearch and Kibana.

## Notes
- This configuration is suitable for development and testing purposes. Configure security features and additional settings as required for production environments.

## Stay Connected

Connect with us on social media and stay updated with the latest news and developments:

- [LinkedIn](https://www.linkedin.com/in/ashwanicse/)
- [Leetcode](https://leetcode.com/ashwani__kumar/)
- [Topmate](https://topmate.io/ashwanikumar)

## Subscribe to our Newsletter
Stay ahead of the curve by subscribing to our LinkedIn newsletter:
- [Subscribe Now](https://www.linkedin.com/newsletters/7084124970443767808/)

Experience the future of e-commerce with CommerceNexus - where innovation meets efficiency!
