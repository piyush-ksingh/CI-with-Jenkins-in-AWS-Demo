pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                git url: 'https://github.com/piyush-ksingh/CI-with-Jenkins-in-AWS-Demo'
            }
        }
        stage("build & SonarQube analysis") {
            steps {
                withSonarQubeEnv('sonarqube_server') {
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
    }	
}
}
