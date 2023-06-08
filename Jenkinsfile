pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
                stage('checkout') {
                    steps {
                        git branch:'main',url:'https://github.com/Haritha-gitt/backend.git'
                    }
                }
                stage('build'){
                   steps{
                        bat 'mvn clean package'
                    }
                }
                stage('test'){
                    steps{
                        bat 'mvn test'
                    }
                }
            }
}
