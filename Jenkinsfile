pipeline{
	agent any
	environment{
	    dockerRegistry = "vinaysh259/test"
	    dockerCred = 'dockre-hub'
	    dockerImage = ''
	}

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
			
		stage('Maven Build'){
			steps {
			sh 'mvn clean package'
			}
			
		 }
		 
		 stage('Docker Image Build'){
		 	steps{
		 		script{
		 		    dockerImage = docker.build dockerRegistry + ":BUILD_NUMBER"
		 		}
		 	}
		 }
		 
		 stage('Deploy Docker Image'){

		                   steps{
		                       
		                       script{
		                           docker.withRegistry('',dockerCred){
		                               dockerImage.push()
		                           }

		                       }

		                   }

		               }
 		 		
	}
}