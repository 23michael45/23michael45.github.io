##Train And Save Model Then Copy From Host To Docker 
* docker cp .\saved_model.pb containerID:/tmp/arbitrary-style-export/1/saved_model.pb
* docker cp .\variables containerID:/tmp/arbitrary-style-export/1/variables
* docker start -i containerID

##Exit Docker Shell And Commit Container To Image
# docker commit containerID gcr.io/tensorflow-serving-208710/arbitrary-style
* gcloud docker -- push gcr.io/tensorflow-serving-208710/arbitrary-style


##Start Serving From Docker Shell
* bazel-bin/tensorflow_serving/model_servers/tensorflow_model_server --port=9000 --model_name=arbitrary-style --model_base_path=/tmp/arbitrary-style-export &> arbitrary_style_log &


##Add inception_k8s.yaml
* Add command above to yaml file


##Run Yaml At Kubernate
* kubectl create -f inception_k8s.yaml