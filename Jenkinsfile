pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
	
	environment {
		HTTP_PROXY = http://10.155.224.26:3128
		HTTPS_PROXY = http://10.155.224.26:3128
	}
	
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}