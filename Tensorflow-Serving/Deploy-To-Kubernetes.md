##Deploy To Kubernetes
* gcloud auth login --project=tensorflow-serving
* gcloud container clusters create inception-serving-cluster --project=tensorflow-serving-208710
* gcloud config set container/cluster inception-serving-cluster
* gcloud container clusters get-credentials inception-serving-cluster

##Commit And Push Docker Image
* docker tag 23michael45/inception_serving gcr.io/tensorflow-serving-208710/inception
* gcloud docker -- push gcr.io/tensorflow-serving-208710/inception

##Create Kubernetes Deployment and Service
* kubectl create -f tensorflow_serving/example/inception_k8s.yaml
* 注意yaml:image: gcr.io/tensorflow-serving-208710/inception      
* 注意yaml:args:
        - ./bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server
          --port=9000 --model_name=inception --model_base_path=/tmp/inception-export
* kubectl get deployments
* kubectl get pods
* kubectl get services
	NAME                    CLUSTER-IP       EXTERNAL-IP       PORT(S)     AGE
	inception-service       10.239.240.227   104.155.184.157   9000/TCP    1m
* 取到External-IP
* 客户端： python tensorflow_serving/example/inception_client.py --server=35.236.157.121:9000 --image=./Xiang_Xiang_panda.jpg

