pipeline {
    agent any
    environment {
        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
    }
    stages {
        stage("clone code"){
            steps{
               git credentialsId: 'git_credentials', url: 'https://github.com/krunalbhoyar/hello-world.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
                sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@52.90.98.65:/opt/tomcat/webapps"
                 
                }
            }
        }
    }
}
