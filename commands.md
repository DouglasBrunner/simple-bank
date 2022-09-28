
go test -v -cover ./...

go run src/main.go

mockgen -package mockdb -destination db/mock/store.go udemy.bank/db/sqlc Store

migrate -path db/migrations -database "postgresql://root:secret@localhost:5432/simple_bank?sslmode=disable" -verbose down

migrate -path db/migrations -database "postgresql://root:secret@localhost:5432/simple_bank?sslmode=disable" -verbose up