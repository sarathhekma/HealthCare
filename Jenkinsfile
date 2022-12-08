pipeline {
  agent any
   stages{
       stage('Build Docker Image'){
        steps{
          sh "docker build ./HealthCare -t helloworldapp"
         }
       }  	  
	  stage('DockerHub Push'){
       steps{
         sh "docker run -d -p 8080:80 helloworldapp"
        }
      }  
     stage('post build'){	  
		post {  
		 success { 

				mail to: 'sarath.s@3ktechnologies.com',
				  subject: "Job Success:  '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
				  body: "Check console output at '${env.BUILD_URL}' for furthur details"
				  
			  } 
					  
		 failure { 

				mail to: 'sarath.s@3ktechnologies.com',
				  subject: "Job Failed:  '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
				  body: "Check console output at '${env.BUILD_URL}' for furthur details"
				  
			  } 
		}
    }
}
}