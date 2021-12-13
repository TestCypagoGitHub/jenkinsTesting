pipeline {
environment {
    BRANCH_NAME = "${env.BRANCH_NAME}"
}
agent any
stages{
    stage('Build-Initiator-Info'){
            steps{
                sh 'echo "Send Info"'
            }
    }
    stage('Build') {
        steps{
             catchError {
                sh 'echo "This is build"'
            }
         }
         post {
            always {
            junit allowEmptyResults: false, testResults: "${WORKSPACE}/test-results/*.xml"

            } 
            success {
                echo 'Compile Stage Successful . . .'
            }
            failure {
                echo 'Compile stage failed'
                error('Stopping early…')

             }
    }
   }
  stage ('Deploy To Prod'){
  input{
    message "Do you want to proceed for production deployment?"
  }
    steps {
                sh 'echo "Deploy into Prod"'

              }
        }
  }
   }
