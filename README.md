# Feeds

Self-hosted version of the [Miniflux](https://miniflux.app/index.html) RSS feed reader.

## Local Setup

- Install and run the `latest stable` version of [Docker](https://docker.com/)
- Copy [.env.sample](.env.sample) to `.env` (Git ignored) and edit as needed
- Then start the Docker Containers: `docker compose up -d`
- Visit `http://localhost:8080` (or change `8080` to the number you set in the `PORT` variable)

## Commands

- Start the Docker Containers: `docker compose up -d`
- Stop the Docker Containers: `docker compose down`

## Links

- [Code repository](https://github.com/miniflux/v2)
- [Docker documentation](https://miniflux.app/docs/docker.html)

## Infrastructure

This project uses [Railway](https://railway.com/) for infrastructure.

Setup manually:

1. Login to [Railway Dashboard](https://railway.com/dashboard)
2. Create a new project
3. Add a new service named `db-postgres`: `Database > PostgreSQL`
4. Wait for that service to create and start
5. Add a new service named `app-miniflux`: `Docker Image > miniflux/miniflux`
6. Follow the below steps

In the `app-miniflux` service, go to the `Variables` tab, then click `Raw Editor`.

Copy over the below section (using your own values for the `ADMIN_` prefixed variables):

```
ADMIN_USERNAME="abc"
ADMIN_PASSWORD="aaaabbbb3333"
CREATE_ADMIN="1"
DATABASE_URL="${{db-postgres.DATABASE_URL}}"
RUN_MIGRATIONS="1"
```

In the `app-miniflux` service, go to the `Networking > Public Networking` section.

Click `Generate Domain` or use your own via the `Custom Domain` option.

To finalise the setup, click the `Deploy` button at the top of the screen.
