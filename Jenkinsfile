pipeline {
    agent any
        stages {
            stage('deploy to nexus') {
                steps {
                    withCredentials([usernamePassword(credentialsId: 'nexus', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASSWORD')]) {
                        sh 'mvn clean deploy --settings=/var/jenkins_home/workspace/nexus_testpipeline/settings.xml -DskipTests '
                        }
                    }
                }
            }
    }
    