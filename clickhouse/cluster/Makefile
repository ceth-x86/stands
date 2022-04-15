clean:
	docker-compose down
	docker volume ls --filter name=cluster* -q | xargs docker volume rm
	docker volume ls --filter name=clickhouse* -q | xargs docker volume rm

start:
	docker-compose up

attach:
	docker exec -it ch_sub_1 bash
