pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
				echo '${env.BUILD_NUMBER}'
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
}