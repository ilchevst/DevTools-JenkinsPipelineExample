pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Sentrance/DevTools-JenkinsPipelineExample'
                echo 'Building..'
            }
        }

        stage('Unit tests') {
            steps {
                echo 'Testing what have to be tested'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying some shit'
            }
        }
        stage('Complete') {
            steps {
                echo 'Job Complete or not complete!'
            }
        }
    }
}
