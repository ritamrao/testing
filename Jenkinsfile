pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
              
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
            
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
       
                echo 'Analyzing code...'
            }
        }
        stage('Security Scan') {
            steps {
             
                echo 'Performing security scan...'
            }
        }
        stage('Deploy to Staging') {
            steps {
          
                echo 'Deploying to staging...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
     
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
   
                echo 'Deploying to production...'
            }
        }
    }

    post {
        always {
            script {
                def log = currentBuild.rawBuild.getLog(1000).join('\n')
                emailext(
                    to: 'ritam22001@gmail.com',
                    subject: "Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.currentResult}",
                    body: """<p>Pipeline ${currentBuild.fullDisplayName} completed with status: ${currentBuild.currentResult}</p>
                             <p>Build Log:</p><pre>${log}</pre>""",
                    attachLog: true
                )
            }
        }
    }
}
