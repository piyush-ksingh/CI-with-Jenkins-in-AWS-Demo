pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                git url: 'https://github.com/piyush-ksingh/CI-with-Jenkins-in-AWS-Demo'
            }
        }
        stage('Maven Build') {
            steps {
                 withEnv(["MVN_HOME=/opt/maven"]) {
                     sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
            }
	}    
	
    }	
}
}
