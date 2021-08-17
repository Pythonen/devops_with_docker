FROM golang:1.16-alpine

WORKDIR /app

COPY ./example-backend/ .

RUN go mod download

EXPOSE 8080

RUN go build

ENV PORT=8080

CMD ./server
