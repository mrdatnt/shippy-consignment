build:
	protoc --proto_path=$GOPATH/src:. --micro_out=. --go_out=. proto/consignment/consignment.proto
	protoc -I. --go_out=plugins=micro:. \
		proto/consignment/consignment.proto

	GOOS=linux GOARCH=amd64 go build
		docker build -t shippy-consignment ./
run:
	docker run -p 50051:50051 \
	    -e MICRO_SERVER_ADDRESS=:50051 \
	    shippy-consignment