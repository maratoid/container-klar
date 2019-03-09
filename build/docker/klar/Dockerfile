FROM buildpack-deps as builder

ARG KLAR_VERSION=2.4.0
RUN curl -L https://github.com/optiopay/klar/releases/download/v${KLAR_VERSION}/klar-${KLAR_VERSION}-linux-amd64 -o /klar \
	&& chmod +x /klar

FROM alpine:3.8
LABEL maintainer   "Samsung SDS - Marat G. <maratoid@gmail.com>"
LABEL purpose      "klar driver for CoreOS Clair"

RUN apk add --no-cache ca-certificates
COPY --from=builder /klar /klar

ENTRYPOINT ["/klar"]
