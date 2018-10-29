pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo env.BUILD_NUMBER
				bat "echo #define BUILD_COUNTER %BUILD_NUMBER%"
			}
        }
        stage('Test') {
            steps {
                echo 'Testing..'
				bat "test.bat"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            emailext subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'", body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p><p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",recipientProviders: [[$class: 'DevelopersRecipientProvider']]
        }
    }		
}