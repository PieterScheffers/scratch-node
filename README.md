# Scratch Node.js Docker Images

Smallest Node.js Docker images (<15MB).

## Content

* A fully statically linked and compressed Node.js binary
* An `/etc/passwd` entry for a `node` user

## Images

* `latest`, `11`, `11.5`, `11.5.0` – 14.6 MB
* `10`, `10.13`, `10.13.0` – 14.3 MB
* `8`, `8.12`, `8.12.0` – 13.2 MB
* `6`, `6.14`, `6.14.4` – 11.6 MB

## Usage

```dockerfile
FROM node as builder

WORKDIR /app

COPY package.json package-lock.json index.js ./

RUN npm install --prod

FROM astefanutti/scratch-node

COPY --from=builder /app /

ENTRYPOINT ["./node", "index.js"]
```
