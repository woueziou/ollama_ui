# Ollama Docker Compose

This repository contains a `docker-compose.yaml` file that allows you to deploy both the Ollama server and the WEB UI on a single Docker container using Docker Compose.

## Prerequisites

Before you begin, make sure you have the following installed:

1. [Docker](https://docs.docker.com/engine/install/)

2. [Docker Compose](https://docs.docker.com/compose/install/)


## Installation

To install Ollama, you can follow these steps:

1. Clone this repository on your local computer or server(whatever): `git clone https://github.com/woueziou/ollama_ui.git`
2. Change directory into the cloned repository: `cd ollama-ui`
3. Build the Docker images: `docker-compose build`
4. Start the Docker containers: `docker-compose up -d`

Once the installation is complete, you can access the Ollama web UI by navigating to `http://localhost:5890` in your web browser.



## Getting a New Model

To get a new model, follow these steps:

1. Navigate to the Ollama web UI at `http://localhost:8080` in your web browser.
2. Click on the "New Model" button in the top right corner of the page.
3. Enter the desired name for your new model and click the "Create" button.
4. Your new model will be created and you can start training it using the Ollama web UI.

## Configuration

You can configure the Ollama server and web UI by editing the `docker-compose.yml` file in this repository. For example, you can change the port that the Ollama server listens on by setting the `PORT` environment variable in the `ollama` service block.

```
ollama:
    container_name: ollama
    image: ollama/ollama
    restart: "unless-stopped"
    volumes:
      - ./ollama:/root/.ollama
    expose:
      - "11434"
```

You can also configure the Ollama web UI by editing the `docker-compose.yaml` file . For example, you can change the port that the web UI listens on

```
openwebui:
    image: ghcr.io/ollama-webui/ollama-webui:main
    restart: always
    volumes:
      - ./ollama-webui:/app/backend/data
    ports:
      - "YOUR_PORT:8080"
    environment:
      - OLLAMA_BASE_URL = "ollama"
```

## Troubleshooting

If you encounter any issues during installation or usage, please check the Docker logs for the Ollama server and web UI by running the following commands:

```
docker-compose logs ollama
docker-compose logs ollama-webui
```

You can also use the `docker-compose run` command to execute a command in the Ollama container. For example, you can use the following command to access the Ollama shell:

```
docker-compose run --rm ollama /bin/bash
```

This will open a new terminal session inside the Ollama container, where you can run any Ollama commands. When you are finished, you can exit the container by typing `exit`.


For any assistance feel free to reach me.
Made in 🇹🇬.