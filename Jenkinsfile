pipeline{
    agent any 
    environment {
                  APP_name= " web-app"
                  ENV = "production"
                }
    parameters {
                  choice choices: ['dev', 'test', 'pre-prod', 'prod'], description: 'Deployment', name: 'ENV'
                     }
   stages{
       stage ("Checkout Scm"){
           steps{
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-credentials', url: 'https://github.com/its-sourabh-01/DevOps.git']])
           }
       }
       
       stage ("test"){
           
               when{
                   branch 'main'

               }
               steps{
                   sh "echo this is test stage"
               
           }
       }
       
       stage("build"){
           steps{
               sh 'ls -lrt'
               echo "list out the all the files"
           }
       }
       
       stage ("completed the pipeline"){
           steps{
               sh "echo all the step is build "
           }
       }
       
   }
   

   post {

    success {
        echo 'Pipeline successful'
    }

    failure {
        echo 'Pipeline failed'
    }

    always {
        echo 'Pipeline completed'
    }
    
    }
   
}