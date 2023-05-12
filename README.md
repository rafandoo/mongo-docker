<h1 align="center">Mongo Docker</h1>

## Project description 📝
This is a quick setup for MongoDB, which creates 3 clusters, 1 primary and 2 secondary, in replica set mode.

Comes with:
- Database: `Mongo 5`

## Configuration ⚙️

### Setup
To setup this project, you will need to install Docker. 
Once installed, run the following steps and commands in the shell:

```shell
git clone https://github.com/rafandoo/mongo-docker.git

cd mongo-docker

docker-compose up -d
```

To access the database, use the following command:

```shell
docker exec -it mongo1 /bin/sh

$ mongo --port 30001
```

To setup the replica set, use the following command:

```bash
> rs.initiate(
    {
        _id: "rs01",
        members: [
            { _id: 0, host : "mongo1:30001" , priority: 5},
            { _id: 1, host : "mongo2:30002" , priority: 1},
            { _id: 2, host : "mongo3:30003" , priority: 1}
        ]
    }
)

# To check the status
> rs.status()

# To view the configuration
> rs.conf()

# If you want to add a new node
> rs.add("HOST:PORT")
```

If you want to stop the containers, use the following command:

```shell
docker-compose down
```

## Questions and Improvements

For any question or emprovement please send an e-mail to Shady Smaoui [shady@veloxsolutions.ca](mailto:shady@veloxsolutions.ca).

## License 🔑

The [MIT License](https://github.com/rafandoo/mongo-docker/blob/13172c76240b24fb896acacbf0dab58ac546aea1/LICENSE) (MIT)

Copyright :copyright: 2023 - Rafael Camargo