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

        stage('Code compliance') {
            agent {
                dockerfile {
                    filename 'sonarscan'
                    dir 'dockerfiles'
                    args '-ti -v ./src:/sonar-scanner/src --network host'
                }
            }
            steps {
                echo 'Code compliance tests...'
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