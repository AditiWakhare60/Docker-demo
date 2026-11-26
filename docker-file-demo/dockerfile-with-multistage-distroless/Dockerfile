## 1st stage: build the binary
FROM ubuntu as build

WORKDIR /src

RUN apt-get update && apt-get install -y golang-go

ENV GO111MODULE=off

COPY . .    

RUN CGO_ENABLED=0 go build -o /app .

## 2nd stage: a minimal image with the binary

FROM scratch

COPY --from=build /app /app 

ENTRYPOINT ["/app"]      