# MinIO Docker Setup

This repository contains a Docker Compose configuration for running MinIO, a high-performance object storage solution.

## Prerequisites

- Docker
- Docker Compose

## Configuration

The setup consists of the following files:
- `docker-compose.yml`: Defines the MinIO service configuration
- `minio.env`: Contains environment variables for MinIO authentication

### Ports

- `9000`: MinIO API port
- `9001`: MinIO Console (Web UI) port

### Environment Variables

Create a `.env` file with the following variables:
```env
MINIO_ROOT_USER=username
MINIO_ROOT_PASSWORD=password
```

> **Note**: Make sure to change the default credentials in production environments.

### Storage

The setup uses Docker volumes for persistent storage:
- Volume name: `minio_data`
- Mount point: `/data`

## Usage

### Starting the Service

```bash
docker-compose up -d
```

### Accessing MinIO

- **API Endpoint**: http://localhost:9000
- **Web Console**: http://localhost:9001

### Stopping the Service

```bash
docker-compose down
```

## Security Considerations

1. Always change the default credentials before deploying to production
2. Consider using Docker secrets for sensitive information
3. Review network access and firewall rules

## Monitoring

You can monitor the MinIO service using:
- Docker logs: `docker logs minio`
- MinIO Console web interface at http://localhost:9001

## Backup

The data is persisted in the Docker volume `minio_data`. To backup your data:
1. Stop the MinIO service
2. Backup the Docker volume
3. Restart the service

## Additional Resources

- [MinIO Documentation](https://min.io/docs/minio/container/index.html)
- [MinIO Docker Hub](https://hub.docker.com/r/minio/minio)