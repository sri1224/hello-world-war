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
	 stage('deploy'){
	     steps{
	        sh 'docker rm -f tom1'
	         sh 'docker run -d --name tom1 -p 8085:8080 tomcat:ver1.1'
	     }
	 }
    }
}
