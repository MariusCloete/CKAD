FROM alpine:3.20

RUN apk add --no-cache curl \
    && adduser -D -u 1001 appuser

USER appuser

CMD ["sleep", "3600"]

