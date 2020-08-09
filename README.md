# Redis
![Redis_logo](https://upload.wikimedia.org/wikipedia/en/thumb/6/6b/Redis_Logo.svg/1200px-Redis_Logo.svg.png)
## Table of Contents
 - [What Is Redis](https://github.com/mechano59/Redis/blob/master/README.md#what-is-redis)
 - [Prerequisite](https://github.com/mechano59/Redis/blob/master/README.md#prerequisite)
 - [Installing and Checking Redis](https://github.com/mechano59/Redis/blob/master/README.md#installing-and-checking-redis)
 - [The Frustration and Solution](https://github.com/mechano59/Redis/blob/master/README.md#the-frustration-and-solution)

## What Is Redis
Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache and message broker. It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs, geospatial indexes with radius queries and streams. Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.
## Prerequisite
We will be installing Redis on a Linux (Ubuntu ) based OS. You need to have Administrator privileges in order to properly install this software. And it's is always a good idea to update your machine before doing any installation to avoid any errors. For that, use :
```
sudo apt update
sudo apt upgrade
```
## Installing and Checking Redis
In order to install redis, you first need to download the tar.gz file from their [website](https://redis.io/download). 

![download_redis_stable](https://github.com/mechano59/Redis/blob/master/images/download_redis_stable.png)

**Note that** : You can also use `sudo apt-get install redis-server` to install Redis but that might install a much older version which might not be ideal for our purpose.

After the download is finished,navigate to the directory and extract the file. In my case it's in the **Downloads** folder.

    cd Downloads
    tar xvzf redis-6.0.6.tar.gz

![extract](https://github.com/mechano59/Redis/blob/master/images/extract.png)

After the file is extracted, navigate to the directory and run the following command: 

    cd redis-6.0.6
    make

![make_in_redis](https://github.com/mechano59/Redis/blob/master/images/make_in_redis-6.0.6.png)

 It's also a good idea to run the `make test` command in order to check the files.
 And you are done! (Mostly, just wait and see. ) now you can run the Redis server from the redis-6.0.6 directory using the command : 
 
    src/redis-server

![run_server](https://github.com/mechano59/Redis/blob/master/images/run_server.png)

And you will see the Redis server up and running and ready for connections.

![the_server](https://github.com/mechano59/Redis/blob/master/images/the_server.png)

You can open another Terminal window in the same redis-6.0.6 directory and enter the following command to run Redis client : 

    src/redis-cli

![redis_client](https://github.com/mechano59/Redis/blob/master/images/run_redis_client.png)

You will see the IP and default port that the server is running on which is 127.0. 0.1 and 6379. You can also run the command `info server` to see information about the server. 

![check_redis](https://github.com/mechano59/Redis/blob/master/images/check_redis.png)

In order to close both the server and the client use the following command from the Redis client : 

    shutdown save
    quit

![cli_shutdown](https://github.com/mechano59/Redis/blob/master/images/cli_shutdown_save.png)

![server_exit](https://github.com/mechano59/Redis/blob/master/images/redis_server_exit.png)

## The Frustration and Solution
You might have noticed that we are running the server and the client from a certain directory (redis-6.0.6) rather than from wherever we want. That's because we can't run it from wherever we want. At least not yet. 
You see, we just extracted and built executable programs and libraries from source code. But we did not installed it in our system. That's why we can not run it from anywhere. To change that, just go to the redis-6.0.6 directory and run the following command : 

    sudo make install

![make_install](https://github.com/mechano59/Redis/blob/master/images/make_install.png)

And that's it! Now you can run the Redis server and the client from anywhere on your PC by just using `redis-server` or `redis-cli`.
