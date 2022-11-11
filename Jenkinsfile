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
		

	stage("Quality Gate"){
		steps{
         		timeout(time: 1, unit: 'HOURS') {
              			def qg = waitForQualityGate()
              			if (qg.status != 'OK') {
                  			error "Pipeline aborted due to quality gate failure: ${qg.status}"
              			}
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

