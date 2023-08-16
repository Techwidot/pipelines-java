pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
            git branch:'main',
                url:'https://github.com/Techwidot/pipelines-java.git'

            }            
        }

        stage('Build') {
            steps{
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
                // Run Maven on a Unix agent.
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
        }

        stage('Deploy') {
            steps {
                echo "Deploy stage started >>>>"
                deploy adapters: [tomcat9 (
                    credentialsId: 'tomcat',
                    path: '',
                    url: 'http://20.231.91.8:8088/'
                )],
                contextPath: 'tomcat',
                onFailure: 'false',
                war: '**/*.war'
            }
            
            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.war'
                }
            }
        }
    }
}
