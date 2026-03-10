# ChatCenter Deployment

This project contains a POS-CMS and API built with PHP, deployed using Docker Compose on Dokploy.

## Services

- **POS-CMS**: Web interface at pos-cms.core-hub-plex.cloud
- **API**: REST API at api-pos-cms.core-hub-plex.cloud
- **MySQL**: Database service

## Setup

1. Ensure Docker and Docker Compose are installed.
2. Clone the repository.
3. Run `docker-compose up --build` to start the services.
4. Access the POS-CMS at pos-cms.core-hub-plex.cloud and API at api-pos-cms.core-hub-plex.cloud (configure DNS accordingly).

## Environment Variables

Configure database connection in `.env`:

- DB_HOST=db
- DB_NAME=pos
- DB_USER=user
- DB_PASS=password

## Deployment on Dokploy

1. Upload the project to your Git repository.
2. In Dokploy, create a new project and connect to the repo.
3. Use the provided `docker-compose.yml`.
4. In Dokploy UI, configure custom domains:
   - For POS-CMS service: pos-cms.core-hub-plex.cloud
   - For API service: api-pos-cms.core-hub-plex.cloud
5. Ensure DNS points to your Dokploy instance.

The database will be created and initialized automatically using the `pos.sql` script.
