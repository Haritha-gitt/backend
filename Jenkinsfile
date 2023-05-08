pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
    ARTIFACTORY_URL = "http://15.207.111.35:8082/artifactory"
    ARTIFACTORY_USERNAME = "credentials('gtr')"
    ARTIFACTORY_PASSWORD = "credentials('Gtr@2023')"
    }
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
        stage('Publish to Artifactory') {
            steps {
                script {
                    def server = Artifactory.server(ARTIFACTORY_URL)
                    def buildInfo = Artifactory.newBuildInfo()

                    server.publishBuildInfo(buildInfo)

                    server.upload(
                        "sample/springboot-backend-0.0.1-SNAPSHOT.jar",
                        "springboot-backend-0.0.1-SNAPSHOT.jar",
                        buildInfo: buildInfo
                    )
                    server.publishBuildInfo(buildInfo)
                }
            }
        }
    }
}
