pipeline {
     agent { 
        node {
            label ''
            }
      }
     triggers {
        pollSCM '*/1 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                echo "Building Done"
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                echo "Testing Done"
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "Delivery Done"
                '''
            }
        }
    }
      post {
        always {
            emailext (
                subject: "Jenkins Build Notification: ${currentBuild.fullDisplayName}",
                body: """<p>Build Pipeline Notification</p>
                         <p>Project: ${env.JOB_NAME}</p>
                         <p>Build Number: ${env.BUILD_NUMBER}</p>
                         <p>Build Status: ${currentBuild.currentResult}</p>
                         <p>Check console output at ${env.BUILD_URL} to view the results.</p>""",
                to: 'vluha@mathworks.com'
            )
        }
    }
}
