pipeline{
    agent any
    stages{
        stage("Git Checkout"){
            steps{
                git credentialsId: 'Git_HUB', url: 'https://github.com/mindeyl/maven-project.git'
            }
        }
        stage("MVN Build"){
            steps{
               bat '''mvn clean package'''
            }
        }
        
        stage("Deploy Build"){
            steps{
              sshagent(['tomcat-new']) {
               sh """
                   scp -o StrictHostKeyChecking=no  target/webapp.war  ec2-user@43.204.237.152:/opt/tomcat9/webapps
                               
                   ssh ec2-user@43.204.237.152 /opt/tomcat9/bin/shutdown.sh
                  
                   ssh ec2-user@43.204.237.152 /opt/tomcat9/bin/startup.sh
               """
              }
            }
        }
    }
 }
