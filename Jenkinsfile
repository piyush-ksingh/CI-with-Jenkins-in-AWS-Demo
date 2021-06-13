pipeline {
    agent any
    stages {
        stage('Git') {
            steps {
                git url:https://github.com/piyush-ksingh/CI-with-Jenkins-in-AWS-Demo
            }
        stage('Maven Build') {
            steps {
                 withEnv(["MVN_HOME=$mvnHome"]) {
                     sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
            }
	stage('Sonar Scan') {
            steps {
                echo 'Hello World'
            }
        stage('Push to artifactory') {
            steps {
                echo 'Hello World'
            }
	stage('Deploy to tomcat') {
            steps {
                echo 'Hello World'
            }
        }
    }	
}
