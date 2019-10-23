pipeline {
    options {
        newContainerPerStage()
        timeout(time: 30, unit: 'MINUTES')
    }

    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Sentrance/DevTools-JenkinsPipelineExample'
                echo 'Building..'
            }
        }
        stage('Code compliance') {
            def sonarScannerImage = docker.build("sonar-scanner-image", "./dockerfiles/sonarscan")
            sonarScannerImage.withRun('-ti -v ./src:/can/src --network host') {
            sh 'pwd'
            }
        }

        stage('Unit tests') {
            steps {
                echo 'Testing....'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}