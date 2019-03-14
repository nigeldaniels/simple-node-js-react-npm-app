pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
  
    environment { 
 	CI = 'true'
    }   
  
stages {
     
	stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }

	stage('mytest') {
	    steps {
		sh './jenkins/scripts/test.sh' 
            }
	}

	stage('Deliver') { 
 	    steps { 
		sh './jenkins/scripts/deliver.sh' 
		input message: 'Finished using the web site? (Click "proceed" to continue)' 
		sh './jenkins/scripts/kill.sh' 
	    }
	
	}

    }
  }

