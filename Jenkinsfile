pipeline{
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts : '**/target/*.war'
                }
            }
        }
        stage('Deploy to Server'){
            steps{
deploy adapters: [tomcat9(credentialsId: 'd197859c-24a4-4f84-929c-eff6a07817ba', path: '', url: 'http://16.16.26.32:9090/')], contextPath: null, war: '**/*.war'            }
        }
    }
}
