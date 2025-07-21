# Valkey

![Build 8, scan & push](https://github.com/Polarix-Containers/valkey/actions/workflows/build-8.yml/badge.svg)
![Build 7, scan & push](https://github.com/Polarix-Containers/valkey/actions/workflows/build-7.yml/badge.svg)

### Features & usage
- Built on the [official image](https://github.com/valkey-io/valkey-container), to be used as a drop-in replacement.
- Unprivileged image: you should check your volumes' permissions (eg `/data`), default UID/GID 200010.

### Sample Docker Compose config

```
  valkey:
    container_name: valkey
    image: ghcr.io/polarix-containers/valkey:8
    restart: unless-stopped
    volumes:
      - ./valkey:/data:Z
    healthcheck:
      test: ["CMD-SHELL", "valkey-cli ping | grep PONG"]
      interval: 15s
      timeout: 5s
    user: "200010:200010"
    read_only: true
    security_opt:
      - "no-new-privileges=true"
    cap_drop:
      - ALL
```

### Licensing
- The code in this repository is licensed under the Apache license. 😇
- The image is built on `docker.io/valkey/valkey`, which is under the BSD license. Copyright to the base image belongs to LF Projects LLC.
- Any image built by Polarix Containers is provided under the combination of license terms resulting from the use of individual packages.
