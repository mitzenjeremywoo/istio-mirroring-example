Please clone and then run following command to test 

create namespace 
kubectl create ns test 

enable istio injection 
kubectl label namespace test istio-injection=enabled

Deploy 2 different version of httpbin - v1 and v2

kubectl apply -f .\httpbin.yaml -n test

kubectl apply -f .\httpbin-v2.yaml -n test

Deploy the httpbin-gateway 
kubectl apply .\httpbin-gateway.yaml -n test


Run a few curl http://localhost 
At this point you can check to see the logs for your pods. 

kubectl logs your-v1-pod-name -n test 

there should be output and no output/request going into podv2

now run 

kubectl apply .\httpbin-gateway-v2.yaml -n test

kubectl logs your-v1-pod-name -n test 
kubectl logs your-v2-pod-name -n test 

The logs exists for both pods. 

