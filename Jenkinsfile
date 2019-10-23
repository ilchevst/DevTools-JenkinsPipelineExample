pipeline {
    agent {
//         docker {
//             image 'sonarqube'
//             args '-d --name sonarqube -p 9000:9000'
//         }
    }

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

        sh 'pwd'
        def sonarScannerImage = docker.build("sonar-scanner-image", "./dockerfiles/sonarscan")
        sonarScannerImage.withRun('-ti -v ./src:/can/src --network host') {
            stage('Code compliance') {
                steps {
                    echo 'Code compliance tests..'
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