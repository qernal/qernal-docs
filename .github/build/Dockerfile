FROM alpine:3.18 as builder

ARG MINISERVE_VERSION="0.24.0"

RUN apk add curl
RUN curl --location https://github.com/svenstaro/miniserve/releases/download/v${MINISERVE_VERSION}/miniserve-${MINISERVE_VERSION}-x86_64-unknown-linux-musl --output miniserve && chmod +x miniserve

# miniserve with qernal docs
FROM scratch

COPY --from=builder /miniserve /
COPY ./ ./output

EXPOSE 8080
CMD ["/miniserve", "--index", "index.html", "output/"]