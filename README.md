# A basic Docker configuration for a Rails app

## Overview

The `Dockerfile` provides a basic image based on `ruby`.

The `docker-compose.yml` provides the following services:
- a `web` service serving your rails application (built from Dockerfile)
- a `webpack_dev_server` service serving your assets from webpack (built from Dockerfile)
- a `redis` server (built from official `redis` docker image)
- a `database' server (built from official `postgresql` docker image)

## Configure to your needs

You can change database name in `.env/development/database`.

## Adapt project's database configuration

```yaml
-- config/database.yml
default: &default
  adapter: postgresql
  encoding: unicode
  # For details on connection pooling, see Rails configuration guide
  # https://guides.rubyonrails.org/configuring.html#database-pooling
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  host: <%= ENV.fetch("DATABASE_HOST") %>
  username: <%= ENV.fetch("POSTGRES_USER") %>
  password: <%= ENV.fetch("POSTGRES_PASSWORD") %>
  database: <%= ENV.fetch("POSTGRES_DB") %>
  variables:
    statement_timeout: 5000
```
