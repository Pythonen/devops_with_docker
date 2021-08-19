FROM golang:1.16-alpine

WORKDIR /app

COPY ./example-backend/ .

EXPOSE 8080

RUN go build && rm -rf example-backend/

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000

CMD ./server
