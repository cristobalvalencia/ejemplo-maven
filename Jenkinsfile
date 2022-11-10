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
    		git 'https://github.com/foo/bar.git'
  	}
  	stage('SonarQube analysis') {
    		def scannerHome = tool 'SonarScanner 4.0';
   		withSonarQubeEnv('Sonar') { // If you have configured more than one global server connection, you can specify its name
      		sh "${scannerHome}/bin/sonar-scanner"
    		}
  	}
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
