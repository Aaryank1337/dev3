pipeline {
    agent any
    tools {
        maven 'Default'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Tomcat Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '1cb9aa9c-ca44-4258-a90a-91fc6943bcc3', path: '', url: 'http://localhost:9999/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
