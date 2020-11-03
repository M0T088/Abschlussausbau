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
                configFileProvider([configFile(fileId: '288a6038-67c3-45be-aecd-42bf286ed2a3', variable: 'MAVEN_GLOBAL_SETTINGS')]){
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
                configFileProvider([configFile(fileId: '288a6038-67c3-45be-aecd-42bf286ed2a3', variable: 'MAVEN_GLOBAL_SETTINGS')]){
                sh 'mvn clean deploy -gs ${MAVEN_GLOBAL_SETTINGS} -DskipTests'
                }
            }
        }
        stage('Tomcat Deploy') {
            steps {
                configFileProvider([configFile(fileId: '288a6038-67c3-45be-aecd-42bf286ed2a3', variable: 'MAVEN_GLOBAL_SETTINGS')]){
                sh 'mvn tomcat7:redeploy -gs ${MAVEN_GLOBAL_SETTINGS} -DskipTests'
                }
            }
        }
    }
}