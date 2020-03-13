# Requirements
- docker(docker-compose)
- nc
- tee
- curl
- mysql-client
- redis-client

# Set up
1. docker-compose up -d

- mysql listen on 3306
- redis listen on 6379
- nginx listen on 8888

# HTTP
1. nc -l 11111 < fifo | tee request.log | nc localhost 8888 | tee fifo > responce.log
1. tail -f request.log 
1. tail -f responce.log
1. curl localhost:11111

1. nc -l 11111 < fifo | tee request.log | nc localhost 8888 | tee fifo > responce.log # tail log file
1. open localhost:11111

# Redis
1. nc -l 11111 < fifo | tee request.log | nc localhost 6379 | tee fifo > responce.log # tail log file
1. redis-cli -p 11111 

try `ping`, `set name hoge`, `get name`

# Mysql
1. nc -l 11111 < fifo | tee request.log | nc localhost 3306 | tee fifo > responce.log # tail log file
1. mysql -h 127.0.0.1 -u root -P 11111 -p # press just enter when asked password (root password is empty)

try `show databases`, `create database hoge`

