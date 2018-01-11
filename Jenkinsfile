pipeline {
    agent any
    stages{
        stage('build'){
            steps{
              echo "clean package begin"
              sh 'mvn clean package'
              echo "clean package end"
            }
            post
            {
                success {
                   echo "Now Archiving ........"
                   archiveArtifacts artifacts: '**/*.war'
                   echo "Finishing Archiving........"
                }
            }
        }
        stage('Deploy to Staging'){
            steps{
                 build job: 'Deploy-to-staging'
            }
        }

        stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve production Deployment?'
                }
                 build job: 'Deploy-to-prod'
            }
            post
                        {
                            success {
                               echo "code deployed to production."

                            }
                             failure {
                                 echo "Deployment failed"

                            }
                        }
        }

    }
}