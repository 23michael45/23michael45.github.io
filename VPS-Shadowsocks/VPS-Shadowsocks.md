##Vultr Website https://my.vultr.com/ 
* Create Servers (ubuntu)
* Get IP Password   (vultr server ip)
* XShell to Server Shell
* sudo apt-get update
  apt-get install python-pip
  pip install shadowsocks
  
* 如果出现Command "python setup.py egg_info" failed with error  
	解决方案
	sudo python -m pip install --upgrade --force pip
	sudo pip install setuptools==33.1.1 

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
  
* ssserver -c /etc/shadowsocks.json -d start   #也可能没有 -d
* ssserver -c /etc/shadowsocks.json -d stop    #也可能没有 -d
* ubuntu 开机启动
	sudo vi /etc/rc.local
	在 exit 0 这一行的上边加入： /usr/local/bin/ssserver –c /etc/shadowsocks.json start
	/usr/local/bin/ssserver也有可能在/usr/bin/sserver 可用find -name ssserver查找一下安装在哪里顾




* Client Setup
  服务器地址：vultr server ip
  服务器端口:2018
  密码：12345678
  代理端口:1080(不变)
 
  右下角点 enable system proxy

 


