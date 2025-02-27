# Use the official Go image as a builder
FROM golang:1.21-alpine as builder

# Set the working directory inside the container
WORKDIR /app

# Copy the Go module files first (for efficient caching)
COPY go.mod go.sum ./
RUN go mod download

# Copy the rest of the application code
COPY . .

# Build the application binary with static linking
# RUN CGO_ENABLED=0 go build -o auth-api
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api .

# Use a distroless static image for the final container
# FROM gcr.io/distroless/static-debian11

FROM alpine:latest

# Set the working directory in the new container
WORKDIR /app

# Copy the built binary from the builder stage
COPY --from=builder /app/auth-api .

# Expose the port (default to 8081)
EXPOSE 8081

# Run the application
CMD ["./auth-api"]