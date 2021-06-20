pipeline {
    agent any
    stages {
        stage("build & SonarQube analysis") {
            steps {
                withSonarQubeEnv('sonarqube_server') {
                   sh 'mvn clean package sonar:sonar'
                }
            }
        }
        stage("Artifacts upload/download") {
            steps {
               rtServer (
                  id: 'Artifactory-server',
                  url: 'http://35.232.179.217:8081/artifactory',
		  username: 'jenkins',     
		  password: 'AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX'
               )
            }   
	}	    
    }	
}
