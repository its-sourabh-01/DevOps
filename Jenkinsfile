pipeline{
        agent any
        parameters {
                    string defaultValue: 'main', description: 'Deployed the project', name: 'Branch'
                    choice choices: ['dev ', 'prod', 'pre-prod', 'test'], description: 'Deployed project based on the choice', name: 'Deployment '

                    }

        stages{
            stage{
                steps{
                    '''
                    echo "BRanch name is : ${params.Branch}"
                    echo Depolyment choice is : ${params.Deployment}
                    
                    '''

                }
            }
        }
}