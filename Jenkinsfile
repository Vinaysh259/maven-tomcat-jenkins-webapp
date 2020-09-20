pipeline{
	agent any
	//environment{
	  //  dockerRegistry = "vinaysh259/test"
	   // dockerCred = 'dockre-hub'
	   // dockerImage = ''
	//}

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
		 
		 stage('Docker Build and Push'){
							 environment{
							     dockerCred = credentials('docker-hub')
							     dockerRegistry = "vinaysh259/test"
							 }
							
							steps{
							     sh 'docker build -t=webapp1'
		                         sh 'docker tag webapp1 ${dockerRegistry}:webapp1'
		                         sh 'docker login -u ${dockerCred_USR} -p ${dockerCred_PSW} docker.io'
		                         sh 'docker push ${dockerRegistry}:webapp1'    
							}

		                    
		                     }


		 
		// stage('Docker Image Build'){
		 	//steps{
		 		//script{
		 		//    dockerImage = docker.build("Webapp:${env.BUILD_ID}")
		 	//	}
		 //	}
		// }
		 
	//	 stage('Deploy Docker Image'){

//		                   steps{
//		                       
//		                       script{
//		                           docker.withRegistry('',dockerCred){
//		                               dockerImage.push(LATEST)
//		                           }
//
//		                       }
//
//		                   }
//
//		               }
		 		
	}
}
