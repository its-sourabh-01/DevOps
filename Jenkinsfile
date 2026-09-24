pipeline{
    agent any 
    parameters {
        choice (choices: ['dev','qa' ,'prod'] ,
                description: "Deployment environment",
                name: 'Env'  
             )
    }

      environment {
                APP_NAME = "web-app"
                }

    stages{
        stage ("checkout scm"){
            steps{
                git branch : 'main' , url: 'https://github.com/its-sourabh-01/DevOps.git' ,
                credentialsId: 'github-credentials'
                echo "checkout the code from github"

            }
        }


        stage ("build"){
            steps{
                sh "echo this is build stage"
                sh "echo the application name is ${APP_NAME}"
            }
           }

        stage ("test"){
            steps{
                echo "Running tests"
            }
        }

        stage ("Deploy"){
            steps{
                echo "Deploying the application to ${Env} environment"
            
            script{

            try {
                    sh "echo deployment to ${Env} environment"
                }
                catch (Exception e) {
                    echo "Deployment failded due to ${e.getMessage()}"
                }
            }
            
        }
    }

    post {
        success {
            echo "Pipeline successful"
        }

        failure {
            echo "Pipeline failed"
        }

        always {
            echo "Pipeline completed"
        }
    }
}