pipeline{
    agent any
    stages{
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
        }
        stage("Nexus Upload"){
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'devops-app', classifier: '', file: 'target/devops-app.war', type: 'war']], credentialsId: 'nexus6pm', groupId: 'in.javahome', nexusUrl: '54.87.20.107:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'devops-app', version: '1.0'
            }
        }
        stage("Dev Deploy"){
            steps{
                dir('ansible'){
                    sh "ansible-playbook -i dev devops-app-deploy.yml"
                }
            }
        }
    }
}