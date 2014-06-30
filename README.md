nginx-rabbitmq
==============
This version would be better: <br />
https://github.com/AlanWangWP/nginx-amqp





This module is used to forward data stream in http GET request to RabbitMQ. In this module, nginx will take values of rum and send them to RabbitMQ.
For example, if request is : localhost/test?rum=test&v=0.9, nginx would send "test" to RabbitMQ

Installation
============
1. Download openresty: http://openresty.org/
2. Unzip source and go to unzipped directory in terminal
3. Type:	./configure --with-luajit && sudo make && sudo make install
4. Install RabbitMQ-C library: https://github.com/alanxz/rabbitmq-c    <br /> Follow the instructions to install rabbitmq-c
5. Put amqp.lua and amqp-util.lua to /usr/local/share/luajit-2.1.0-alpha/      <br /> You can change this directory if you want. But you also need to change lua_package_path in nginx.conf file
6. Use above nginx.conf file to override /usr/local/openresty/nginx/conf/nginx.conf    <br /> You can change your ip, exchange, queue, user, password variables for RabbitMQ in nginx.conf file
7. Restart your nginx and open terminal to type: curl -i localhost/test?rum=test&v=0.9    <br /> If you get similar reply like this, then your data is successfully sent to RabbitMQ

HTTP/1.1 200 OK<br /> 
<br /> 
Server: openresty/1.7.0.1<br /> 
Date: Wed, 25 Jun 2014 18:07:11 GMT<br /> 
Content-Type: application/octet-stream<br /> 
Transfer-Encoding: chunked<br /> 
Connection: keep-alive<br /> 
Content-type: text/plain<br /> 
<br /> 
Sent:[test] to RabbitMQ.<br /> 




==============
The lua code is from https://github.com/tcoram/rabbitmq-lua
