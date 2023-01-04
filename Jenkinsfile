pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven3/bin:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/jallu225/hello-world.git'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        stage("deploy-dev"){
            steps{
                sshagent(['tomcat-new']) {
                sh """
                    scp -o StrictHostKeyChecking=no target/myweb.war  ec2-user@172.31.34.197:/home/ec2-user/tomcat/webapps/
                    
                    ssh ec2-user@172.31.34.197 /home/ec2-user/tomcat/bin/shutdown.sh
                    
                    ssh ec2-user@172.31.34.197 /home/ec2-user/tomcat/bin/startup.sh
                
                """
            }
            
            }
        }
    }
}
