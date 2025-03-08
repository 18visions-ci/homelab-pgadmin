# homelab-pgadmin# homelab-pgadmin

This repository contains the configuration and deployment scripts for setting up pgAdmin in a homelab environment using Docker Compose. pgAdmin is a popular administration and development platform for PostgreSQL databases.

## Configuration

The repository includes two environment configuration files:

- `.env.dev`: Configuration for the development environment.
- `.env.prod`: Configuration for the production environment.

Both files define the following environment variables:

- `PGADMIN_PORT`: The port on which pgAdmin will be accessible.
- `PGADMIN_DEFAULT_EMAIL`: The default email address for pgAdmin login.
- `PGADMIN_DEFAULT_PASSWORD`: The default password for pgAdmin login.

## Actions Integration

This repository uses GitHub Actions for automated deployment:

- **Development Deployment**: The [deploy-dev.yaml](.github/workflows/deploy-dev.yaml) workflow is triggered on pushes to the `main` branch. It deploys the development environment using the `.env.dev` configuration file.
- **Production Deployment**: The [deploy-prod.yaml](.github/workflows/deploy-prod.yaml) workflow is manually triggered via the GitHub Actions interface. It deploys the production environment using the `.env.prod` configuration file.

Both workflows perform the following steps:

1. Checkout the repository.
2. Setup SSH keys for secure deployment.
3. Copy the `docker-compose.yaml` and the appropriate `.env` file to the target server.
4. Deploy the pgAdmin service using Docker Compose.
5. Cleanup SSH keys.

For more details, refer to the respective workflow files in the `.github/workflows/` directory.