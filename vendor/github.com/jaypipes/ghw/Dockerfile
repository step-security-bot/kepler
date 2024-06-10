FROM golang:1.15-buster@sha256:414340e7bfee1b13c72c59e9b0df5488b83b6a5c99c2d806509304ca7ef71350 as builder
WORKDIR /go/src/github.com/jaypipes/ghw

# Force the go compiler to use modules.
ENV GO111MODULE=on
ENV GOPROXY=direct

# go.mod and go.sum go into their own layers.
COPY go.mod .
COPY go.sum .

# This ensures `go mod download` happens only when go.mod and go.sum change.
RUN go mod download

COPY . .

RUN CGO_ENABLED=0 go build -o ghwc ./cmd/ghwc/

FROM alpine:3.7@sha256:8421d9a84432575381bfabd248f1eb56f3aa21d9d7cd2511583c68c9b7511d10
RUN apk add --no-cache ethtool

WORKDIR /bin

COPY --from=builder /go/src/github.com/jaypipes/ghw/ghwc /bin

CMD ghwc
