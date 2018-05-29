### Docker上安装Tensorflow-Serving并制作镜像
## Docker相关
- 安装Docker后，设置Setting里的镜像为国内加速镜像http://7b316225.m.daocloud.io
- docker pull ubuntu
- docker images 查看镜像ID
- docker run -it 镜像ID   bash    //第一次一定要这样运行，否则再start不会到命令行
- docker ps -a查看容器ID
- exit后可用 docker start 容器ID   |   docker  attach 容器ID   重新进入容器
- docker import / export 可导入导出容器   |   docker save /load可导入导出镜像

## Ubuntu相关
- RUN apt-get update && apt-get install -y sudo && rm -rf /var/lib/apt/lists/*
- sudo apt-get update && sudo apt-get install -y  build-essential  curl   libcurl3-dev    git  libfreetype6-dev    libpng-dev       libzmq3-dev         pkg-config      python-dev       python-numpy   python-pip     software-properties-common     swig  zip  zlib1g-dev
- pip install tensorflow-serving-api
- echo "deb [arch=amd64] http://storage.googleapis.com/tensorflow-serving-apt stable tensorflow-model-server tensorflow-model-server-universal" | sudo tee /etc/apt/sources.list.d/tensorflow-serving.list

- curl https://storage.googleapis.com/tensorflow-serving-apt/tensorflow-serving.release.pub.gpg | sudo apt-key add -
- sudo apt-get update && sudo apt-get install tensorflow-model-server
- 如有需要可升级: sudo apt-get upgrade tensorflow-model-server
- git clone https://github.com/tensorflow/serving.git
- cd serving
-  git clone https://github.com/tensorflow/tensorflow.git
-  git clone https://github.com/tensorflow/models.git
## 开启Serving  mnist
- 源码编译
$>bazel build -c opt //tensorflow_serving/model_servers:tensorflow_model_server
$>bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server --port=9000 --model_name=mnist --model_base_path=/tmp/mnist_model/
- PIP PACKAGE
tensorflow_model_server --port=9000 --model_name=mnist --model_base_path=/tmp/mnist_model/
- 源码测试
$>bazel build -c opt //tensorflow_serving/example:mnist_client
$>bazel-bin/tensorflow_serving/example/mnist_client --num_tests=1000 --server=localhost:9000
...
Inference error rate: 10.5%
- PIP 测试
python tensorflow_serving/example/mnist_client.py --num_tests=1000 --server=localhost:9000