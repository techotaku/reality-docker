# reality-docker
Source code of container images for xray reality.

### Usage
```
version: '3'

networks:
  default:
    driver: bridge

services:

  forwarder:
    image: ghcr.io/techotaku/reality-forwarder
    restart: unless-stopped
    environment:
     - REALITY_DEST_HOST=    # reality dest host
    networks:
      - default
    logging:
      driver: "json-file"
      options:
        max-size: "1M"
    ports:
      - "80:8080/tcp"
      - "443:443/udp"

  server:
    image: ghcr.io/techotaku/reality-server
    restart: unless-stopped
    environment:
     - REALITY_UUIDS=    # reality vless UUID, like: (UUID1 UUID2 UUID3), or (UUID)
     - REALITY_DEST_HOST=    # reality dest host
     - REALITY_DOMAINS=    # reality SNI domains, like: (domain1 domain2)
     - REALITY_PRIV_KEY=    # reality private key
     - REALITY_SHORT_IDS=    # reality short IDs, like: (ID1 ID2 ID3 ID4)
    networks:
      - default
    logging:
      driver: "json-file"
      options:
        max-size: "1M"
    ports:
      - "443:443/tcp"
```
