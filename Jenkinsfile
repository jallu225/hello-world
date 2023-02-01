node {
    stage ('Git Checkout'){
       git 'https://github.com/jallu225/hello-world.git' 
    }
    stage ('Unit test') {
        bat 'mvn test'
    }
    stage('Integration Testing'){
        bat "mvn verify -DskipUnitTests"
    }
    stage ('Maven build') {
        bat 'mvn clean install'
    }
}
