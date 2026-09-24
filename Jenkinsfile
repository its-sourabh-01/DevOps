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
                sh "echo this is build stage ${params.Env}"
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
    }
    post {
        success {
            echo "Pipeline successful"
            mail to: 'sourabhpatil00007@gmail.com',
                 subject: "Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The Jenkins pipeline succeeded.\nJob: ${env.JOB_NAME}\nBuild Number: ${env.BUILD_NUMBER}\nURL: ${env.BUILD_URL}"
        }

        failure {
            echo "Pipeline failed"
        }

        always {
            echo "Pipeline completed"
        }
    }
}