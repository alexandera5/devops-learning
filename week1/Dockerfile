FROM golang as builder
WORKDIR /src
COPY go.mod .
COPY cmd .
RUN CGO_ENABLED=0 go build -o app

FROM scratch
ADD ./static /static
COPY --from=builder /src/app .
ENTRYPOINT [ "/app" ]
EXPOSE 8080
