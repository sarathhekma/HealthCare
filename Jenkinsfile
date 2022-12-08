pipeline {
  agent any
   stages{
       stage('Build Docker Image'){
        steps{
          sh "docker build -t helloworldapp ."
         }
       }  	  
	  stage('DockerHub Push'){
       steps{
         sh "docker run -d -p 8081:80 helloworldapp"
        }
      }  
      stage('postbuild')
        {
            steps
            {
               // input 'waiting for approval'
                //sh 'scp **/target/*.war ubuntu@172.31.30.45:/var/lib/tomcat7/webapps'
                echo 'Docker run success'
            }
			post
			{
			success
			{
			echo 'post section'
			mail to: 'sarath.s@3ktechnologies.com',
		    subject: "Job Success:  '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
		    body: "Check console output at '${env.BUILD_URL}' "
			}
			}
        }
	}
}