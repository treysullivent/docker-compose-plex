# Docker Compose for Plex and Kometa Setup

This repository contains Docker Compose configurations to set up and manage multiple services related to a Plex Media Server environment, including Plex itself, Kometa, and other dependent services. The repository also includes a template environment file (`kometa.env.example`) to help you configure these services easily.

## Repository Structure

- **`compose.yaml`**: The main Docker Compose file that defines the services and their configurations.
- **`kometa.env.example`**: A template environment file for the Kometa service. Copy this file to `kometa.env` and fill in your specific environment variables to configure the service properly.
- **`letterboxd.env.example`**: A template environment file for the Letterboxd Plex Sync service. Copy this file to `letterboxd.env` and fill in your specific environment variables to configure the service properly.


## Services

The `compose.yaml` file includes the following services: 

- **Plex**: A media server to stream your media content.
- **Tautulli**: A tool for monitoring Plex server usage.
- **Kometa**: A service that works in conjunction with Plex, providing additional functionality.
- **Imagemaid**: A tool from the Kometa team used to clean up Plex image cache.
- **Letterboxd Plex Sync**: A tool to sync Letterboxd data with Plex.

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started) and [Docker Compose](https://docs.docker.com/compose/install/) installed on your machine.
- Basic knowledge of Docker and Docker Compose.

### Step-by-Step Setup

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/treysu/docker-compose-plex.git
   cd docker-compose-plex
   ```

2. **Configure Environment Files**:
   - Copy the example environment file for Kometa:
     ```sh
     cp kometa.env.example kometa.env
     cp letterboxd.env.example letterboxd.env

     ```
   - Open the `.env` files and fill in the required values to configure the Kometa service properly.

3. **Run Docker Compose**:
   - To start all the services defined in the `compose.yaml` file, use:
     ```sh
     docker compose -f compose.yaml up -d
     ```

4. **Stop and Remove Services**:
   - To stop all running services and remove containers, networks, and volumes:
     ```sh
     docker compose -f compose.yaml down
     ```

### Customization

- **Modify Volumes and Paths**: Adjust the volumes and paths in `compose.yaml` to fit your environment and desired storage locations.
- **Edit `*.env` Files**: Modify the environment variables specific to your setup as needed.

## Environment Variables

The `.env` files should contain all necessary environment variables for the related service to function correctly. 

You should also add a `default.env` file that contains the timezome evnironment varaible. (e.g `TZ=America/Chicago`)

## Health Check and Auto-Restart

The `compose.yaml` file includes configurations for health checks and auto-restart of services. Each service will attempt to restart unless explicitly stopped.

- **Health Check**: A basic health check is set up to check for connectivity using `curl`.
- **Restart Policy**: All services have a restart policy of `unless-stopped`.

## Troubleshooting

- **Environment File Issues**: Ensure all required environment variables in the `.env` files are properly set.
- **Permission Issues**: Ensure Docker has permission to access the volumes and directories specified in `compose.yaml`.
- **Service Logs**: Check logs for individual services using:
  ```sh
  docker compose -f compose.yaml logs <service_name>
  ```

## Contributing

Contributions, issues, and feature requests are welcome!

---

*Happy streaming!*
