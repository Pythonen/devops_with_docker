FROM golang:1.16-alpine as build

WORKDIR /app

COPY ./example-backend/ .

RUN go mod download && go build -o /backend


FROM alpine:latest

COPY --from=build /backend /backend
EXPOSE 8080
ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000

CMD ./backend
