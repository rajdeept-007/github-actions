pipeline {
    agent any
    stages {
        stage("Checkout") {
            steps{
                git branch: 'main',
                url: 'https://github.com/rajdeept-007/github-actions.git'
            }
        }
        stage("Build") {
            steps{
                sh 'mvn clean compile'
            }
        }
        stage("Test") {
            steps{
                sh 'mvn test'
            }
        }
        stage("Package") {
            steps{
                sh 'mvn package'
            }
        }
        stage("Archive Artifacts") {
            steps{
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage("Run") {
            steps{
                sh 'java -cp target/classes App'
            }
        }
    }
}