pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
	
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package -DproxySet=true -DproxyHost=10.155.224.26 -DproxyPort=3128' 
            }
        }
    }
}