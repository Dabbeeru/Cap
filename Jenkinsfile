     pipeline {
	     
	     environment {
    registry = "dilleswari/learning"
    registryCredential = 'Dockerhub'
  }
          agent any
          stages {
              stage('Checkout external proj') {
                steps {
                    git branch: 'master',
                        credentialsId: 'gitlab',
                    url: 'https://github.com/Dabbeeru/Cap.git'
                    
                     
        
                    sh "ls -lat"
                }
        		}
        	
            
              
                stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }

  }
  


			
stage('Building image') {
      steps{
          
          script {
          docker.build registry + ":$BUILD_NUMBER"
        }
          
        
        sh 'docker login -u dilleswari -p l@xmi321'
          sh 'docker push dilleswari/learning:webserver:v1'
          
          
        script {
          docker.build registry + ":$BUILD_NUMBER"
		 sh 'docker build -t dilleswari/webserver:v1 .'
		 sh 'docker images'
		 sh 'docker run -it -d webserver:v1 . '
		
		
		 
		
        
      }
    }
  

     }
     }
     }
     
