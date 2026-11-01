# Tahap 1: Build aplikasi Go
FROM golang:1.27-alpine AS builder

WORKDIR /app

# Salin file konfigurasi module
COPY go.mod go.sum ./

RUN go mod download

# Salin seluruh source code
COPY . .

# Build binary Go dengan ukuran minimal
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
    go build -trimpath -ldflags="-s -w" -o server .

# Tahap 2: Image akhir yang minimal
FROM scratch

WORKDIR /

COPY --from=builder /app/server /server

EXPOSE 50051

ENTRYPOINT ["/server"]
