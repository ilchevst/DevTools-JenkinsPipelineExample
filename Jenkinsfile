pipeline {
    options {
        newContainerPerStage()
        timeout(time: 30, unit: 'MINUTES')
    }

    def sonarScannerImage = docker.build("sonar-scanner-image", "./dockerfiles/sonarscan")
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Sentrance/DevTools-JenkinsPipelineExample'
                echo 'Building..'
            }
        }

        sonarScannerImage.inside('-ti -v ./src:/can/src --network host') {
                stage('Code compliance') {
                    steps {
                        echo 'Code compliance testing...'
                    }
                }
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