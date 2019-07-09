pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
	
    options {
        skipStagesAfterUnstable()
    }
	
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -DproxySet=true -DproxyHost=10.155.224.26 -DproxyPort=3128 -B -DskipTests clean package' 
            }
        }
		
		stage('Test') {
			steps {
				sh 'mvn -DproxySet=true -DproxyHost=10.155.224.26 -DproxyPort=3128 test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.xml'
				}
			}
		}
		
		stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
	}
}