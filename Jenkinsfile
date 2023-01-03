pipeline {
    agent any
    stages {
        stage ('Git Checkout') {
            steps {
                script{
                    git 'https://github.com/jallu225/hello-world.git'
                }
            }
        }
        stage ('MVN Build') {
            steps {
                script{
                    sh 'mvn clean install'
                }
            }
        }
    }
