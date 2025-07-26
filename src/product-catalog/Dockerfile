FROM golang:1.22-alpine as builder

WORKDIR /usr/src/app

COPY . .

RUN go mod download

RUN go build -o product-catalog .

FROM alpine AS release

WORKDIR /usr/src/app

COPY ./products ./products

COPY --from=builder /usr/src/app/product-catalog .

EXPOSE ${PRODUCT_CATALOG_PORT}

ENV PRODUCT_CATALOG_PORT 5001

ENTRYPOINT ["./product-catalog"]

