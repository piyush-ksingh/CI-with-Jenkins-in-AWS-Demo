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
                  url: 'http://35.188.4.139:8081/artifactory',
		  username: 'jenkins',     
		  password: 'AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX'
               )
            }   
	}
	stage("Deploy to tomcat") {
            steps {
                sshagent(['tomcat_deploy']) {
                    sh 'ssh -v -o StrictHostKeyChecking=no singh_piyushkr79@34.70.7.142'
		    sh 'cd /opt/tomcat/webapps'
		    sh 'wget -O jenkins:AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX http://35.188.4.139:8081/artifactory/example-repo-local/ci/jenkins/aws/project/1.0-RAMA/project-1.0-RAMA.war'
		}
	    }    
	}	    
    }	
}
