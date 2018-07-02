##Windows Shell里调用Python client.py 请求Docker里的tensorflow serving
* Windows Shell里运行 docker run -it -p 127.0.0.1:9000:9000  imageID
* Docker Shell里运行 bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server --port=9000 --model_name=inception --model_base_path=/tmp/inception-export &> inception_log &
*  Windows Shell里运行  python tensorflow_serving/example/inception_client.py --server=127.0.0.1:9000 --image=./Xiang_Xiang_panda.jpg




