# REDIS DATABASE
![1a1d75af-2c5d-415c-adb4-6de7525dc2a4.png](1a1d75af-2c5d-415c-adb4-6de7525dc2a4.png)

## INTRODUCTION
- Redis is an open source in-memory data structure store.
- Used as a database, cache and message brocker.
- Redis holds its entire database in memory.
- Disk is used for persisten data storage.
- It is a NoSQL database and follow a key-value store concepts.

- It supports robust data structure like string, hashes, list, sets,sorted sets, bitmap, hyperloglogs.
- Redis can be connected with various clients.

## INSTALATION ON DOCKER
```yaml
  redis-dev:
    container_name: redis-db
    image: redis:alpine3.18
    restart: always
    ports:
      - "6379:6379"
      - "8001:8001"
    volumes:
      - ./volume/redis:/data
    networks:
      - bacsystem
```

```link
https://redis.io
```
```bash
$ redis-server
```
```bash
$ redis-cli
```
```bash
$ ping "Hello"
```
```bash
$ quit
```
### Commans redis
```link
https://redis.io/commands/
```

### The Redis Data Storage
- Redis is a Key based data structure.
- Redis is in the family of database called "Key-Values-stores".
- A key means is a way to store and retrive values
```bash
$ get key
$ set key value
```

#### Example:
```bash
# Set and Get Information
$ redis-cli
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian"
# OK
$ get dd1ceced-1754-486a-bf22-1161c6f92026
# "Christian"
# Delete key
$ del dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 1 
$ get dd1ceced-1754-486a-bf22-1161c6f92026
# (nil)
#  How to check if a key exists or not
$ exists dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 0
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian"
# OK
$ exists dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 1
```

```bash
# How to define keys with expiration
# TTL 
# - The command returns -2 if the key does not exist.
# - The command returns -1 if the key exists but has no associated expire.
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian" ex 120
# OK
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 32
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) -2
# Change expire
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian" ex 120
# OK
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 117
$ expire dd1ceced-1754-486a-bf22-1161c6f92026 10
# (integer) 1
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 8 
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) -2
```

```bash
# How to remove expiration from a key
# PERSIST Syntax
$ PERSIST key
# Return
# - 1 if the timeout was removed.
# - 0 if key does not exist or does not have an associated timeout.

$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian" ex 120
# OK
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 108
$ persist dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) 1
$ ttl dd1ceced-1754-486a-bf22-1161c6f92026
# (integer) -1
```
```bash
# Key Spaces
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "Christian"
# OK
$ get dd1ceced-1754-486a-bf22-1161c6f92026
# "Christian"
$ set dd1ceced-1754-486a-bf22-1161c6f92026 "David"
# OK
$ get dd1ceced-1754-486a-bf22-1161c6f92026
# "David" 
```