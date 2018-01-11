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

    }
}