pipeline {
	agent { label 'd-1' }
    stages {
	    
       stage('checkout') {
            steps {
                sh 'sudo rm -rf hello-world-war'
	sh 'git clone https://github.com/sri1224/hello-world-war.git'	
              }
        }
	 stage('build') {
	
            steps {
                dir('hello-world-war'){
                  sh 'pwd'
                sh 'ls'
            
                sh 'docker build -t tomcat:ver1.1 .'  
                }
            }
	 }
	    stage('push'){
	     steps{
	        sh 'docker tag tomcat:ver1.1 sri1224/test1:1.0 '
	         sh 'docker push sri1224/test:1.0'
	     }
	 }
	 stage('deploy'){
	     steps{
	        sh 'docker rm -f tom1'
	         sh 'docker run -d --name tom1 -p 8085:8080 sri1224/test1:1.0'
	     }
	 }
    }
}
