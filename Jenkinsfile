pipeline {
    agent any
    stages {
        stage ('Git Checkout') {
            steps {
                script{
                    git branch: 'main', url: 'https://github.com/jallu225/demo-counter-app.git'
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
}
