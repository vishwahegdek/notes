# Inspecting Running Docker Containers

When you need to check a running Docker container's configuration, database connections, or mounted volumes, use these commands:

## Identify the Container

```bash
# List all running containers
docker ps

# Filter containers by name, image, etc.
docker ps | grep [FILTER_TERM]
```

## Inspect Container Configuration

```bash
# Get detailed JSON information about the container
docker inspect CONTAINER_ID

# Get specific information using format template
docker inspect -f '{{json .Config}}' CONTAINER_ID
```

## Check Volume Mounts

```bash
# List all mounts in compact format
docker inspect -f '{{.Mounts}}' CONTAINER_ID

# Display mounts in a more readable format
docker inspect -f '{{range .Mounts}}{{.Source}} -> {{.Destination}}{{printf "\n"}}{{end}}' CONTAINER_ID
```

## Check Network and Connection Information

```bash
# Get all environment variables (may include connection details)
docker inspect -f '{{.Config.Env}}' CONTAINER_ID

# Get network settings
docker inspect -f '{{json .NetworkSettings}}' CONTAINER_ID

# View network connections inside container
docker exec CONTAINER_ID netstat -tulpn

# Check logs for connection information
docker logs CONTAINER_ID | grep -i [SEARCH_TERM]
```

## Access Container for Direct Inspection

```bash
# Get an interactive shell inside the container
docker exec -it CONTAINER_ID bash  # or sh, depending on the container

# Once inside the container, you can:
# Check configuration files
cat /path/to/config/file

# View environment variables
env

# Find configuration files
find / -name "*.conf" 2>/dev/null
```

## Container Port Mapping

```bash
# Check which ports are exposed and mapped
docker port CONTAINER_ID

# Alternative way to see port mappings
docker inspect -f '{{range $p, $conf := .NetworkSettings.Ports}}{{$p}} -> {{(index $conf 0).HostPort}}{{printf "\n"}}{{end}}' CONTAINER_ID
```

## Resource Usage

```bash
# Check container's resource usage
docker stats CONTAINER_ID --no-stream
```

These commands will help you determine:
- Which volumes are mounted and their path mappings
- Network connections and database connection information
- Port mappings between host and container
- Other configuration details about your running container