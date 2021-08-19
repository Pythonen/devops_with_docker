FROM golang:1.16-alpine as build

WORKDIR /app

COPY ./example-backend/ .

#RUN go mod download && go build -o /backend
RUN go mod download && CGO_ENABLED=0 go build -ldflags="-w -s" -o /backend

# This is already pretty 
FROM scratch
COPY --from=build /backend /backend
EXPOSE 8080
ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:5000
ENTRYPOINT ["./backend"]

