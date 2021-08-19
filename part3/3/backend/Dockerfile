FROM golang:1.16-alpine

WORKDIR /app

COPY ./example-backend/ .

RUN go mod download

EXPOSE 8080

RUN go build

RUN adduser -S appuser

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000

USER appuser

CMD ./server
