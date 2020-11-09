pipeline {
    agent any
    stages {
		stage('Compile') {
			steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Sonar Verify') {
            steps {
                configFileProvider([configFile(fileId: '3626fad1-bf93-4fb9-b209-780540db7c86', variable: 'MAVEN_GLOBAL_SETTINGS')]){
                sh 'mvn -gs ${MAVEN_GLOBAL_SETTINGS} verify sonar:sonar -DskipTests'
                }
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }
        stage('Nexus Deploy') {
            steps {
                configFileProvider([configFile(fileId: '3626fad1-bf93-4fb9-b209-780540db7c86', variable: 'MAVEN_GLOBAL_SETTINGS')]){
                sh 'mvn clean deploy -gs ${MAVEN_GLOBAL_SETTINGS} -DskipTests'
                }
            }
        }
        stage('Tomcat Deploy') {
                steps {
                    ansiblePlaybook colorized: true, disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'deploy.yml'
                }
            }
        }
    }
}