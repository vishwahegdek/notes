# Inspecting Running Odoo Docker Container

When you've deployed an Odoo container and need to check its database connection and addon code mount paths, use these commands:

## Identify the Odoo Container

```bash
# Find your running Odoo container
docker ps | grep odoo
```

## Inspect Container Configuration

```bash
# Get detailed information about the container (replace CONTAINER_ID with your actual container ID)
docker inspect CONTAINER_ID
```

## Check Volume Mounts (Addon Code Paths)

```bash
# List all mounts in compact format
docker inspect -f '{{.Mounts}}' CONTAINER_ID

# Display mounts in a more readable format
docker inspect -f '{{range .Mounts}}{{.Source}} -> {{.Destination}}{{printf "\n"}}{{end}}' CONTAINER_ID
```

## Check Database Connection Information

```bash
# Get all environment variables (including DB connection info)
docker inspect -f '{{.Config.Env}}' CONTAINER_ID

# Check logs for database connection information
docker logs CONTAINER_ID | grep -i database
```

## Access Container for Direct Inspection

```bash
# Get an interactive shell inside the container
docker exec -it CONTAINER_ID bash

# Once inside the container, you can:
# Check Odoo configuration
cat /etc/odoo/odoo.conf

# View environment variables related to the database
env | grep -i db
```

These commands will help you determine:
- Which database your Odoo instance is connected to
- Where your addon code is being mounted from your host system
- Other configuration details about your running container