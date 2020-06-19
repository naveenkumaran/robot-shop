FROM golang:1.2.17

ENV GOPATH=/go

COPY src/ /go/src/github.com/dispatch

WORKDIR /go/src/github.com/dispatch

RUN dep init && \
	dep ensure && \
    go build -o bin/gorcv

CMD bin/gorcv
