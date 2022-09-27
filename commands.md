
go test -v -cover ./...

go run src/main.go

 mockgen -package mockdb -destination db/mock/store.go udemy.bank/db/sqlc Store