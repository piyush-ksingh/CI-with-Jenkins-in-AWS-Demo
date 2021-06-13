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
               rtServer (
                  id: 'Artifactory-server',
                  url: 'http://34.136.221.214:8081/artifactory'
		  username: 'jenkins'     
		  password: 'AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX'
               }
	       rtDownload (
                  serverId: 'Artifactory-1',
                  spec: '''{
                      "files": [
                       {
                          "pattern": "example-repo-local/ci/jenkins/aws/project/1.0-RAMA/project-1.0-RAMA.war",
                          "target": "artifact_download/"
                       }
                      ]
                  }'''
            }   
	}
    }	
}
