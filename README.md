# A basic Docker configuration for a Rails app

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
