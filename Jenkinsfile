pipeline{
        agent any
        parameters {
                    string defaultValue: 'main', description: 'Deployed the project', name: 'Branch'
                    choice choices: ['dev ', 'prod', 'pre-prod', 'test'], description: 'Deployed project based on the choice', name: 'Deployment '

                    }

        
         stages{
            stage (test){
                steps{
                    
                   sh "echo Branch name is : ${params.Branch}"
                    sh "echo Deployment choice is : ${params.Deployment}"
                    

                }
            }
        }
}