# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

- Ruby version : 3.0.0

- System dependencies :

  - rails 7.0.3
  - mysql2

- Database configuration
  - database.yml and set up username and password
  - rails db:create
  - rails db:migrate
  - How to create controller

* rails g controller controller name
  
  
  Rails Database
  The last step is to allow the Rails application to access the database. If you run Docker Compose right now, both containers will start but Rails will have a database connection error.

To fix this, modify your config/database.yml file so that it looks something like:

default: &default
adapter: postgresql
encoding: unicode
host: db
username: postgres
pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
timeout: 5000
host: db allows the rails application to connect to the database container. I also specified the database username because the root role doesn’t exist on the postgres:9.6-alpine image.

With these changes to the database.yml file, you can start your application by running:

$ docker-compose build
$ docker-compose up
docker-compose build builds the images on your machine. docker-compose up starts the containers based on those images.

You should now be able to browse to http://localhost:3000 and see your application running.
