# Sample multi-container application

All the commands should be run from the root folder of the project.

## Before running the rails application...

* Clone this repository
* We are using a volume to cache gems and another volume to cache node modules. Run the following commands to warm
  up those cached volumes:

```bash 
> docker-compose run --rm web bundle install
> docker-compose run --rm web rails yarn:insall
```


## Running the rails application

* Create the databases

```bash
> docker-compose run --rm web rails db:create
```

* Load the database schema:

```bash
docker-compose run --rm web rails db:schema:load
```

* Seed the database

```bash
> docker-compose run --rm web rails db:seed
```

* Run the rails application

```bash
> docker-compose up
```

* Point your browser to `localhost:3000` as usual


## Shutdown the rails application

```bash
> docker-compose down
```

If you want to clear all the volumes run

```bash 
> docker-compose down -v
```

If you run this last command, you will erease all the persisted data **including the database**, the cached gems and the cached node modules.
