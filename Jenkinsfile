pipeline {
	agent { label 'java' }
    stages {
	    
       stage('build') {
            steps {	
	sh 'mvn clean package'	
              }
        }
	 stage('copy') {
            steps {	
	sh 'cp /home/slave-5/jenkins/workspace/hello1/target/hello-world-war-1.0.0.war /opt/tomcat9/webapps/'	
              }
        }    
    }
}
