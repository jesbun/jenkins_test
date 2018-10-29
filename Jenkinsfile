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
            emailext body: "subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME},
                ${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']]"}
    }		
}