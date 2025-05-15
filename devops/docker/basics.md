# Docker Basic Commands

A quick reference guide for commonly used Docker commands.

## Container Operations

```bash
# Run a container
docker run [OPTIONS] IMAGE [COMMAND]
docker run -d -p 8080:80 nginx  # Run nginx in detached mode, mapping port 8080 to 80

# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Stop a container
docker stop CONTAINER_ID

# Start a stopped container
docker start CONTAINER_ID

# Restart a container
docker restart CONTAINER_ID

# Remove a container
docker rm CONTAINER_ID

# Execute a command in a running container
docker exec -it CONTAINER_ID bash  # Get interactive shell

# Enter the PostgreSQL database inside the container
psql -h db -U odoo postgres
```


## Image Operations

```bash
# List available images
docker images

# Pull an image from Docker Hub
docker pull IMAGE_NAME:TAG

# Build an image from Dockerfile
docker build -t NAME:TAG PATH
docker build -t myapp:1.0 .  # Build from current directory

# Remove an image
docker rmi IMAGE_ID

# Show image history
docker history IMAGE_ID
```

## System Management

```bash
# View Docker system info
docker info

# Check Docker disk usage
docker system df

# Remove unused data (containers, networks, images)
docker system prune

# View container logs
docker logs CONTAINER_ID

# Display container resource usage
docker stats
```

## Network Operations

```bash
# List networks
docker network ls

# Create a network
docker network create NETWORK_NAME

# Connect a container to a network
docker network connect NETWORK_NAME CONTAINER_ID
```

## Volume Operations

```bash
# List volumes
docker volume ls

# Create a volume
docker volume create VOLUME_NAME

# Remove a volume
docker volume rm VOLUME_NAME
```
### 🧹 One-liner to remove all unused volumes safely:
```bash
sudo docker volume prune
```