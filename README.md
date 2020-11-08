# Install go-junit-report
```sh
  go get -u github.com/jstemmer/go-junit-report
```

# Steps

## Run test
```sh
  # cd store-service
  go mod download
  go test ./... -v 2>&1 | go-junit-report > report.xml
```

## set up application
```sh
  # cd ..
  docker-compose up -d --build --force
```

## run api test
```sh
  # cd test/api
  robot checkout-success-template
  # cd ../..
  docker-compose down
```