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
        stage('SCM') {
			steps{
				git 'https://github.com/foo/bar.git'
			}
		}
		stage('SonarQube analysis') {
			steps{
				withSonarQubeEnv(credentialsId: 'f225455e-ea59-40fa-8af7-08176e86507a', installationName: 'My SonarQube Server') { // You can override the credential to be used
				sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
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

