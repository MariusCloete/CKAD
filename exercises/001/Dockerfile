FROM 18-alpine

COPY . .
WORKDIR /app
RUN apk add --no-cache python3 py3-pip && \
    pip3 install --no-cache-dir -r requirements.txt

ENTRYPOINT [" npm ", "start"]