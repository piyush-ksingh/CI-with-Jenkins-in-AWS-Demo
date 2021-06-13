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
                  url: 'http://34.136.221.214:8081/artifactory',
		  username: 'jenkins',     
		  password: 'AKCp8jQcwjZvC9KmZUMjuZhBNd2C4K76aLvxABoCAfHQ3qv1QTdDeuBsoxijbSrhXPd4cphkX'
               )
	       rtDownload (
                  serverId: 'Artifactory-server',
                  spec: '''{
                      "files": [
                       {
                          "pattern": "example-repo-local/ci/jenkins/aws/project/1.0-RAMA/*.war",
                          "target": "artifact_download/"
                       }
                      ]
                  }'''
	       )
            }   
	}
	stage("Deploy to tomcat") {
            steps {
                sshagent(['tomcat_deploy']) {
                    sh 'scp -o StrictHostKeyChecking=no artifact_download/example-repo-local/ci/jenkins/aws/project/1.0-RAMA/*.war singh_piyushkr79@34.70.139.158:/opt/tomcat/webapps'
		}
	    }    
	}	    
    }	
}
