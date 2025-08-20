# Proglog

A simple JSON/HTTP server for managing logs with produce and consume operations.

## Usage

Start the server:
```bash
go run cmd/server/main.go
```

### Produce records (POST)
```bash
curl -X POST localhost:8080 -d '{"record": {"value": "TGV0J3MgR28gIzEK"}}'
# {"offset":0}

curl -X POST localhost:8080 -d '{"record": {"value": "TGV0J3MgR28gIzEK"}}'
# {"offset":1}

curl -X POST localhost:8080 -d '{"record": {"value": "TGV0J3MgR28gIzEK"}}'
# {"offset":2}

curl -X POST localhost:8080 -d '{"record": {"value": "TGV0J3MgR28gIzEK"}}'
# {"offset":3}
```

### Consume records (GET)
```bash
curl -X GET localhost:8080 -d '{"offset": 0}'
# {"record":{"value":"TGV0J3MgR28gIzEK","offset":0}}

curl -X GET localhost:8080 -d '{"offset": 1}'
# {"record":{"value":"TGV0J3MgR28gIzEK","offset":1}}

curl -X GET localhost:8080 -d '{"offset": 3}'
# {"record":{"value":"TGV0J3MgR28gIzEK","offset":3}}
```
