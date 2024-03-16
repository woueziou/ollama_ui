# Ollama Docker Compose

This repository contains a `docker-compose.yml` file that allows you to deploy both the Ollama server and the Ollama web UI on a single Docker container using Docker Compose.

## Installation

To install Ollama, you can follow these steps:

1. Clone this repository: `git clone https://github.com/ollama-ai/ollama-docker-compose.git`
2. Change directory into the cloned repository: `cd ollama-docker-compose`
3. Build the Docker images: `docker-compose build`
4. Start the Docker containers: `docker-compose up -d`

Once the installation is complete, you can access the Ollama web UI by navigating to `http://localhost:8080` in your web browser.

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
  image: ollamaai/ollama:latest
  ports:
    - "8080:8080"
  environment:
    - PORT=8080
```

You can also configure the Ollama web UI by editing the `Dockerfile` in the `ollama-webui` directory. For example, you can change the port that the web UI listens on by setting the `PORT` environment variable in the `EXPOSE` directive.

```
EXPOSE 8080
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