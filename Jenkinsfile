node {
    stage ('Git Checkout'){
       git 'https://github.com/jallu225/hello-world.git' 
    }
    stage ('Unit test') {
        bat 'mvn test'
    }
    stage ('mvn build') {
        bat 'mvn clean install'
    }
}
