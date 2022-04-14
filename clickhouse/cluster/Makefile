rm-volumes:
	docker volume ls --filter name=cluster* -q | xargs docker volume rm
	docker volume ls --filter name=clickhouse* -q | xargs docker volume rm
