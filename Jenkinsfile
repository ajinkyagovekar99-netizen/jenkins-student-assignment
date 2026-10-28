pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compiling application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests... Pass!'
                // Simulated test report (writeFile works on both Windows and Linux agents)
                writeFile file: 'test-report.txt', text: "Unit tests: PASSED\nBuild: #${env.BUILD_NUMBER}\n"
            }
        }

        stage('Package') {
            steps {
                // build-info.txt with the current build number and timestamp
                writeFile file: 'build-info.txt',
                          text: "Build Number: ${env.BUILD_NUMBER}\nTimestamp: ${new Date()}\n"
                echo 'Generated build-info.txt'
                archiveArtifacts artifacts: 'build-info.txt, test-report.txt', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build successful! Ready for release.'
        }
        failure {
            echo 'Build failed. Check the console output.'
        }
    }
}
