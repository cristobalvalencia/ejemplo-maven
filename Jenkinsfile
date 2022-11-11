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
				sh 'mvn clean package sonar:sonar'			
			}
		}
		

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

