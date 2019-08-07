# Simple Redis sentinel setup

If you need to test your system with High-availability Redis Sentinels, you need to setup sentinels locally.

This repo provide simple script and step to set it up.

Steps

1. Install Redis. For Mac OS I recommend `brew install redis`
2. Run start.sh

### Detail explanation of the setup

In this setup, we have 3 Redis instances

1. Master Redis at port 6380
2. Slave Redis at port 6379
3. Redis Sentinels at port 26379

The slave Redis is a replicate of Master redis. It's act as a fallback Redis.

Now if you use any driver and connect to sentinels at 26379, now you have High-availability setup for Redis.

The most simple test you can run is to connect to sentinels, shutdown the Redis at 6380 port by using `SHUTDOWN` command and see if your connection still works. It should take around 500 milliseconds to automatically reconnect to Redis at port 6379.
