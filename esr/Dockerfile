FROM golang:latest

RUN apt-get update && apt-get upgrade -y && apt-get install -y git

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY *.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -o esr .

COPY systemconfig.json .

EXPOSE 20102

CMD ["./esr"]
