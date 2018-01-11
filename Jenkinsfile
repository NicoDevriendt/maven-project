pipeline {
    agent any
    stages{
        stage('build'){
            steps{
              sh 'mvn clean package'
            }
            post
            {
                succes {
                   echo "Now Archiving ........"
                   archiveArtifacts artifacts '**/target/*.war'
                }
            }
        }
              
    }
}