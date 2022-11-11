pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh "./mvnw clean compile -e"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
		stage('SonarQube analysis') {
			steps{
				withSonarQubeEnv('Sonar') {
               			sh 'mvn clean package sonar:sonar'
              			}			
			}		
		}
		stage("Quality Gate") {
            		steps {
              			timeout(time: 1, unit: 'HOURS') {
                			waitForQualityGate abortPipeline: true
              			}
            		}
          	}		
	stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

