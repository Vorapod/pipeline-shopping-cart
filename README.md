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
  docker-compose up -d --build --force-recreate
```

## run api test
```sh
  # cd test/api
  robot checkout-success-template
  # cd ../..
  docker-compose down
```


## จบครั้งที่ 1 ใช้เวลาโดยประมาณ 2 ชั่วโมง
### ปัญหาที่เจอ
1. เสียเวลาในการ set GOPATH เพื่อใช้ go-unit-test
2. รัน api test ไม่ผ่านเพราะเวลารันเทส store-service ยัง start ไม่เสร็จ ทำให้ Fail วิธีแก้คือ ต้องใส่ timeout ไปให้ 60 วิ

### ดีขึ้น
1. เริ่มคิดกระบวนตั้งแต่ต้นยันจบได้ดีขึ้น