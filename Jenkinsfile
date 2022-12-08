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
            withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'user')]) 
             { 
              sh "docker login --username="sarath724" --password=Saipatham724#"
              sh "docker push sarath724/helloworldapp:latest"
            }
        }
       }	  
	    stage('DockerHub Run'){
       steps{
         sh "docker run -d -p 8081:80 helloworldapp"
        }
       }  
      stage('postbuild') {
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
			//mail to: 'saivijayadasami2018@gmail.com',
		    //subject: "Job Success:  '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
		    //body: "Check console output at '${env.BUILD_URL}' "
			}
			}
      }
  }
}