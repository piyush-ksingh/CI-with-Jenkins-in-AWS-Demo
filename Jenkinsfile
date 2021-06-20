pipeline {
    agent any
    stages {
	stage("git checkout") {
            steps {
                git url: 'https://github.com/piyush-ksingh/CI-with-Jenkins-in-AWS-Demo.git'
            }
        }
        stage("build & SonarQube analysis") {
            steps {
                withSonarQubeEnv('sonarqube_server') {
                   sh 'mvn clean package sonar:sonar'
                }
            }
        }
        stage("Artifacts upload") {
            steps {
               rtServer (
                  id: 'Artifactory-server',
                  url: 'http://35.184.25.85:8081/artifactory',
		  username: 'jenkins',     
		  password: 'AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX'
               )
            }   
	}	    
    }	
}
