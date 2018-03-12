pipeline {
 agent any
 stages {
	 stage('Build Automation') {
		 steps {
			 sh '''
			 echo "BUILD NUMBER: ${BUILD_NUMBER}"
			 export KUBECONFIG=/root/.bluemix/plugins/container-service/clusters/mycluster/kube-config-hou02-mycluster.yml
			 kubectl cluster-info
			 '''
		 }
	 }
 }
}