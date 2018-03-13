pipeline {
 agent any
 stages {
	 stage('Kubernetes Deploy') {
		 steps {
			 sh '''
			 echo "Deploy to mycluster"
			 cat apiKey.json
			 bx login --apikey @apiKey.json
			 bx cs region-set us-south
			 #bx cs cluster-config mycluster
			 #export KUBECONFIG=/root/.bluemix/plugins/container-service/clusters/mycluster/kube-config-hou02-mycluster.yml
			 $(bx cs cluster-config mycluster|grep KUBECONFIG)
			 set | grep KUBECONFIG
			 kubectl cluster-info
			 if kubectl describe deployment productpage-v1; then
                echo "Apps already exists, delete first"
                kubectl delete -f bookinfo.yaml
             fi
			 kubectl create -f bookinfo.yaml
			 '''
		 }
	 }
 }
}