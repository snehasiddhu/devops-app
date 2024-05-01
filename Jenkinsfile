pipeline{
    agent any
    stages{
        stage("Maven Build"){
            steps{
                sh "/opt/homebrew/bin/mvn clean package"
            }
        }
        // stage("Nexus Upload"){
        //     steps{
        //         nexusArtifactUploader artifacts: [[artifactId: 'devops-app', classifier: '', file: 'target/devops-app.war', type: 'war']], credentialsId: 'nexus6pm', groupId: 'in.javahome', nexusUrl: '54.87.20.107:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'devops-app', version: '1.0'
        //     }
        // }
        stage("Dev Deploy"){
            steps{
                sh "/Library/Frameworks/Python.framework/Versions/3.10/bin/ansible-playbook -i ansible/dev ansible/devops-app-deploy.yml"
            }
        }
    }
}