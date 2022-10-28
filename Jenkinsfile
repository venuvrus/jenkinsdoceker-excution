pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/venuvrus/jenkinsdoceker-excution.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t jenkins-SPV:latest .' 
                sh 'docker tag jenkins-SPV venuvrus/jenkins-SPV:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push venuvrus/jenkins-SPV:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
