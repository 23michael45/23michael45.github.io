##Vultr Website https://my.vultr.com/ 
* Create Servers (ubuntu)
* Get IP Password   (vultr server ip)
* XShell to Server Shell
* sudo apt-get update
  apt-get install python-pip
  pip install shadowsocks
* create /etc/shadowsocks.json
  vi /etc/shadowsocks.json
  add: (单端口)
  {
	  "server": "0.0.0.0",
	  "server_port": 2018,
	  "password": "12345678",
	  "method": "aes-256-cfb",
	  "local_address": "127.0.0.1",
	  "local_port":1080,
  }
  (多端口)
  {
    "server": "0.0.0.0",
    "port_password": {
        "8381": "password1",
        "8382": "password2",
        "8383": "password3",
        "8384": "password4"
    },
    "timeout": 300,
    "method": "aes-256-cfb"
  }
  
* ssserver -c /etc/shadowsocks.json -d start
* ssserver -c /etc/shadowsocks.json -d stop 


* Client Setup
  服务器地址：vultr server ip
  服务器端口:2018
  密码：12345678
  代理端口:1080(不变)
 
  右下角点 enable system proxy

 


