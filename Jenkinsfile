pipeline {
 agent any
 stages {
	 stage('Setup') {
		 steps {
			 sh '''
			 echo "BUILD NUMBER: ${BUILD_NUMBER}"
			 bx login --apikey apiKey.json
			 bx cs region-set us-south
			 bx cs cluster-config mycluster
			 export KUBECONFIG=/root/.bluemix/plugins/container-service/clusters/mycluster/kube-config-hou02-mycluster.yml
			 kubectl cluster-info
			 '''
		 }
	 }
	 stage('Kubernetes Deploy') {
		 steps {
			 sh '''
			 echo "Deploy to mycluster"
			 kubectl cluster-info
			 kubectl create -f bookinfo.yaml
			 '''
		 }
	 }
 }
}