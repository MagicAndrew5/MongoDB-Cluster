## create a network
docker network create -d overlay petsOverlay

## status services
docker service ls

## command for start docker 
docker stack deploy --compose-file docker-compose.yml app

## get id of container
docker ps

docker exec -it <id_config> sh -c "mongosh < /scripts/init-configserver.js"
docker exec -it <id_shard01> sh -c "mongosh < /scripts/init-shard01.js"
docker exec -it <id_shard02> sh -c "mongosh < /scripts/init-shard02.js"
docker exec -it <id_shard03> sh -c "mongosh < /scripts/init-shard03.js"
docker exec -it <id_shard04> sh -c "mongosh < /scripts/init-shard04.js"
docker exec -it <id_shard05> sh -c "mongosh < /scripts/init-shard05.js"
docker exec -it <id_shard06> sh -c "mongosh < /scripts/init-shard06.js"
docker exec -it <id_shard07> sh -c "mongosh < /scripts/init-shard07.js"

docker exec -it <id_router01> sh -c "mongosh < /scripts/init-router.js"

## command for running shard or router in mongos
docker exec -it <id_router01> mongosh --port 27017

------------------------------------------------------------------------------------------------------------------------------

## shardDb 
sh.enableSharding("<namedb>")

## shardCollection
sh.shardCollection("<namedb>.<namecollection>", {"<field>":"hashed"})

## command for running shard or router in container shell
docker exec -it <id_router01> sh

## import file json
docker cp <percorso_locale_del_file> <nome_contenitore>:<percorso_contenitore>

## import database in router 
mongoimport --jsonArray --db <namedb> --collection <namecollection> --file <namefile>.json

## switch to specific database 
show dbs && use <namedb>

## check distribution 
db.<namecollection>.getShardDistribution()

