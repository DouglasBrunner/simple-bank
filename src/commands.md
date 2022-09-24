postgres: 
	docker run --name postgres12 -p 5432:5432 -e POSTGRES_USER=root -e POSTGRESS_PASS=secret -d postgres:12-alpine

createdb:
	docker exec -it postgres12 createdb --username=root --owner=root simple_bank

dropdb:
	docker exec -it postgres12 dropdb simple_bank

.PHONY: postgres createdb dropdb

	migrate -path db_migrations -database "postgresql://root:secret@localhost:5432/simple_bank?sslmode=disable" --verbose up