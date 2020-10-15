pipeline {
    agent any
        stages {
            stage('deploy to nexus') {
                steps {
                    withCredentials([usernamePassword(credentialsId: 'nexus', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASSWORD')]) {
                        sh 'mvn clean deploy -DskipTests '
                        }
                    }
                }
            }
    }
    