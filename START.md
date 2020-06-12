# Start Ruby on Rails Project on Docker Containers

1. Run Rails and build the project.
    ```shell
    $ docker-compose run web rails new . --force --no-deps --database=postgresql
    $ docker-compose build
    ```

2. Configure the database in `config/database.yaml`.
    ```config/database.yaml
    default: &default
      adapter: postgresql
      encoding: unicode
      host: db
      username: postgres
      password: postgres
      pool: 5

    development:
      <<: *default
      database: myapp_development


    test:
      <<: *default
      database: myapp_test
    ```

3. Execute Rails Server on foreground.
    ```
    $ docker-compose up
    ```

4. Create databases configured in `config/database.yaml`.
    ```
    $ docker-compose run web rake db:create
    ```
