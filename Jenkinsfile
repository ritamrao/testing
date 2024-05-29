pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
            post {
                success {
                    notifyBuild('Build', 'SUCCESS')
                }
                failure {
                    notifyBuild('Build', 'FAILURE')
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
            post {
                success {
                    notifyBuild('Unit and Integration Tests', 'SUCCESS')
                }
                failure {
                    notifyBuild('Unit and Integration Tests', 'FAILURE')
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
            }
            post {
                success {
                    notifyBuild('Code Analysis', 'SUCCESS')
                }
                failure {
                    notifyBuild('Code Analysis', 'FAILURE')
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
            post {
                success {
                    notifyBuild('Security Scan', 'SUCCESS')
                }
                failure {
                    notifyBuild('Security Scan', 'FAILURE')
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
            }
            post {
                success {
                    notifyBuild('Deploy to Staging', 'SUCCESS')
                }
                failure {
                    notifyBuild('Deploy to Staging', 'FAILURE')
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
            post {
                success {
                    notifyBuild('Integration Tests on Staging', 'SUCCESS')
                }
                failure {
                    notifyBuild('Integration Tests on Staging', 'FAILURE')
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
            }
            post {
                success {
                    notifyBuild('Deploy to Production', 'SUCCESS')
                }
                failure {
                    notifyBuild('Deploy to Production', 'FAILURE')
                }
            }
        }
    }

    post {
        always {
            // Final notification with build status
            notifyBuild('Pipeline', currentBuild.currentResult)
        }
    }
}

def notifyBuild(stageName, status) {
    def logFile = "logs/${stageName}-${status}.log"
    archiveArtifacts artifacts: '**/logs/**/*.log', allowEmptyArchive: true

    emailext(
        to: 'ritam22001@gmail.com',
        subject: "${stageName} ${status}: Pipeline ${currentBuild.fullDisplayName}",
        body: """<p>${stageName} completed with status: ${status}</p>
                 <p>Pipeline URL: ${env.BUILD_URL}</p>""",
        attachmentsPattern: logFile
    )
}
