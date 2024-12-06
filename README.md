# Valkey

![Build 8, scan & push](https://github.com/Polarix-Containers/valkey/actions/workflows/build-8.yml/badge.svg)
![Build 7, scan & push](https://github.com/Polarix-Containers/valkey/actions/workflows/build-7.yml/badge.svg)

### Features & usage
- Built on the [official image](https://github.com/valkey-io/valkey-container), to be used as a drop-in replacement.
- Unprivileged image: you should check your volumes' permissions (eg `/data`), default UID/GID 3009.

### Sample Docker Compose config

```
  valkey:
    container_name: valkey
    image: ghcr.io/polarix-containers/valkey:8
    restart: unless-stopped
    volumes:
      - ./valkey:/data:Z
    user: "3009:3009"
    read_only: true
    security_opt:
      - "no-new-privileges=true"
    cap_drop:
      - ALL
```