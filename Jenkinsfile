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
    stage ('sonar analysis') {
        withSonarQubeEnv(credentialsId: 'sonar-token') {            
            bat  "mvn clean package sonar:sonar"
        }
    }
    stage('upload war file to nexus') {
        nexusArtifactUploader artifacts: 
        [
            [
                artifactId: 'maven-project', 
                classifier: '', 
                file: 'target/webapp.war', 
                type: 'war'
                ]
        ], 
        credentialsId: 'sonar-auth', 
        groupId: 'com.example.maven-project', 
        nexusUrl: '192.168.56.112:8081', 
        nexusVersion: 'nexus3', 
        protocol: 'http', 
        repository: 'app-release', 
        version: '1.0-SNAPSHOT'
    }
}
