# mockingbird-example

Demo of [PolarBearAndrew/Mockingbird](https://github.com/PolarBearAndrew/mockingbird)

## Get Started

### Docker Compose

```yaml
version: '3.4'
services:
  envoy:
    image: 'envoyproxy/envoy-dev:b055dd082c0a49525a97cea6604ac1323a55d2fb' # mocking bird is base on envoy,
    volumes:
      - './envoy_config.yaml:/etc/envoy/envoy.yaml'
    ports:
      - '10000:10000'
      - '10001:10001'
    networks:
      - mockingbird-internal
  mockingbird-server:
    image: 'andrewchen20/mockingbird:latest' # mocking bird server
    ports:
      - '4000:4000'
      - '3000:3000'
    networks:
      - mockingbird-internal
networks:
  mockingbird-internal:
    name: mockingbird-internal
```

### Start Servers

1. Mockingbird will running on ```http://localhost:10000/*```
1. Mockingbird GUI admin will running on ```http://localhost:3000/admin```

```sh
$ docker-compose up -d
# or
$ sh start.sh
```
