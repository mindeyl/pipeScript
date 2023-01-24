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
                sh "mvn clean package"
            }
        }
    }
 }
