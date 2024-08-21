@Library("7am-libs") _

pipeline{
    agent any
    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'april1724', credentialsId: 'javahometech', url: 'https://github.com/javahometech/devops-app'
            }
        }
        stage("Maven Build"){
            steps {
                sh '/opt/homebrew/bin/mvn clean package'
            }
        }
        stage("Tomcat Deploy"){
            steps {
                tomcatDeploy("54.82.16.197")
                }
            }
        }
        stage("Tomcat Test Deploy"){
            steps {
                tomcatDeploy("54.82.16.200")
                }
            }
        }
    }
}
