pipeline {
    agent any
    tools {
        jdk 'JDK11'
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Mohsenghafoorydotin/java-hello-world-with-maven-new.git'
            }
        }
        stage('build') {
            steps{
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps{
                sh 'mvn test'
            }
        }
        stage('package') {
            steps{
                sh 'mvn package'
            }
        }
        stage('Deploy to Staging') {
            steps {
                sh 'java -jar target/maigolab_hello-1.0.0.jar &'
            }
        }
        stage('Deploy to Production') {
            steps {
                input message: 'Deploy to Production?', ok: 'Deploy'
                sh 'java -jar target/maigolab_hello-1.0.0.jar &'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
