FROM golang:1.17-alpine AS builder

LABEL stage=gobuilder

ENV CGO_ENABLED 0
ENV GOOS linux
ENV GOPROXY https://goproxy.cn,direct

WORKDIR $GOPATH/src/zero
COPY . .
RUN go mod init && go mod tidy -compat=1.17 &&  go build -ldflags="-s -w" -o /app/client client.go


FROM alpine

RUN apk update && apk add --no-cache tzdata
ENV TZ Asia/Shanghai

WORKDIR /app
COPY --from=builder /app/client /app/client
COPY etc/k8s.yaml /app/

CMD ["./client", "-f", "k8s.yaml"]
