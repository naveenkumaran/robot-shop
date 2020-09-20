FROM golang AS builder
# Install git.
# Git is required for fetching the dependencies.
ENV GOPATH=/go

RUN apt-get update && apt-get install -y go-dep

WORKDIR /go/src/github.com/dispatch

COPY src/ /go/src/github.com/dispatch

RUN dep ensure

FROM golang

WORKDIR /go/src/github.com/dispatch
# Copy from source package exluding dep
COPY --from=builder /go/src/github.com/dispatch /go/src/github.com/dispatch
# Run the  binary.
RUN go build -o bin/gorcv

CMD bin/gorcv
