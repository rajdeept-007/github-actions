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
                bat 'mvn clean compile'
            }
        }
        stage("Test") {
            steps{
                bat 'mvn test'
            }
        }
        stage("Package") {
            steps{
                bat 'mvn package'
            }
        }
        stage("Archive Artifacts") {
            steps{
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage("Run") {
            steps{
                bat 'java -cp target/classes App'
            }
        }
    }
}