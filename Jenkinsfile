pipeline {
	agent none
    stages {
	    
       stage('checkout') {
	       agent { label 'd-1' }
            steps {
                sh 'sudo rm -rf hello-world-war'
	sh 'git clone https://github.com/sri1224/hello-world-war.git'	
              }
        }
	 stage('build') {
	agent { label 'd-1' }
            steps {
                dir('hello-world-war'){
                  sh 'pwd'
                sh 'ls'
            
                sh 'docker build -t tomcat:${BUILD_NUMBER} .'  
                }
            }
	 }
	    stage('push'){
		    agent { label 'd-1' }
	     steps{
	        sh 'docker tag tomcat:${BUILD_NUMBER} sri1224/test1:${BUILD_NUMBER} '
	         sh 'docker push sri1224/test1:${BUILD_NUMBER}'
	     }
	 }
	 stage('deploy'){
		 agent { label 'd-2' }
	     steps{
	        sh 'docker rm -f tom1'
	         sh 'docker run -d --name tom1 -p 8090:8080 sri1224/test1:${BUILD_NUMBER}'
	     }
	 }
    }
}
