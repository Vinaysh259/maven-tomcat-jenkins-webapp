pipeline{
	agent any
	tools{
		maven 'maven-3.6.3'
		}
		
	stages {
	
		stage('Initialize'){
			steps{
			sh '''
				echo "PATH = ${PATH}"
				echo "M2_HOME = ${M2_HOME}"
				'''
				}
			}
			
		stage('Build'){
			steps {
			sh 'mvn clean package'
			}
			
		 }
		 
		 stage('Deployment'){
		 	steps{
		 		deploy(
		 			adapters: tomcat9
		 			war: target/mywebapp.war
		 			contextPath: mywebapp
		 	)
		 
		 }
		}
	}
}