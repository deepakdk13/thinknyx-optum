# Configure the Metrics Server to which is pre requisite for HPA

$ kubectl apply -f 01_metric_server.yaml

# Wait till below command start giving output

$ kubectl top node
$ kubectl top pod

Deployment Application with 1 Replica & Service

$ kubectl apply -f 02_demo_app.yaml

#Create an AutoScale on CPU %

$ kubectl autoscale deployment webapp --min=1 --max=10 --cpu-percent=30

#Genrate a loa using below commands in new terminal

$ kubectl run -it --rm lg-1 --image=busybox /bin/sh
$ while true; do wget -q -O- http://webappsvc; done



# You can check after some time that number of pods will increase to support the increased load, once load reduce they automatically goes down to some or minimum required state

