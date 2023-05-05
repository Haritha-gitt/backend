pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                git branch:'main',url:'https://gitlab.com/haritha-git/sample.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
    }
}
