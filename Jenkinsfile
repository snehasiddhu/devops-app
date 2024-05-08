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
                // Copy war file to remote
                // Stop tomcat on remote
                // Start tomcat on remote
                sshagent(['tomcatdev-7am']) {
                    sh "scp -o StrictHostKeyChecking=no target/devops-app.war ec2-user@54.82.16.197:/opt/tomcat9/webapps"
                    sh "ssh ec2-user@54.82.16.197 /opt/tomcat9/bin/shutdown.sh"
                    sh "ssh ec2-user@54.82.16.197 /opt/tomcat9/bin/startup.sh"
                }
            }
        }
    }
}
