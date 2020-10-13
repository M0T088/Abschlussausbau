pipeline {
    agent any
        stages {
            stage('Testen und Kompilieren') {
                steps {
                    sh 'mvn test' 
                }
            }
            stage("WAR-File erstellen") {
                steps {
                    sh 'mvn clean package -DskipTest'
                }
            }
        
            stage("deploy War-file to tomcat") {
                steps {
                    ansiblePlaybook colorized: true, disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'deploy.yml'
             }
         }
    }
}
    
