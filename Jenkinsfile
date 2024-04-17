pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat7(credentialsId: '8cee57d8-d153-4d30-8bc8-edea36f5fb17', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
