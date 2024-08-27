pipeline{
    agent any 


    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving th Artifacts"
                    archiveArtifacts artifacts :  '**/target/*.war'

                }
            }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '1cb9aa9c-ca44-4258-a90a-91fc6943bcc3', path: '', url: 'http://localhost:9999/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}