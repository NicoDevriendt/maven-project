pipeline {
    agent any
    stages{
        stage('build'){
            steps{
              echo "clean package begin"
              mvn clean package
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

    }
}