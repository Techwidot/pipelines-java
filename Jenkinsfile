pipeline {
    agent any
    stages {
        stage('Prepare') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main',
                    url: 'https://github.com/mycloud-practice/pipeline_test.git'
            }

 

            post {
                success {
                    echo "Preparation is successfull ! :)"
                }
            }
        }

 

        stage('Build'){
            steps{
                echo "Building"
            }

 

            post{
                success{
                echo "Build is succesfull ! :)"
                }
            }
        }

 

        stage('Test'){
            steps{                
                  echo "Testing"
            }
            post{
                success{
                echo "Test done" 
                }
            }
        }

 

        stage("Deploy"){
            steps{
                echo 'Deploying'
            }
            post{
                success{
                    echo "Deployment done"
                }
            }
        }

 

    }
}
