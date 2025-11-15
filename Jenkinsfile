pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kiransuresh-coder/jenkins-build-automation.git'
            }
        }
        stage('Deploy to Apache') {
            steps {
                sh 'sudo cp index.html /var/www/html/index.html'
            }
        }
    }
    post {
        success {
            emailext (
                to: 'kiransr2002@gmail.com',
                subject: "SUCCESS: Jenkins Build #${BUILD_NUMBER}",
                body: "The build was successful!\n"
            )
        }
        failure {
            emailext (
                to: 'kiransr2002@gmail.com',
                subject: "FAILED: Jenkins Build #${BUILD_NUMBER}",
                body: "The build failed.\n\nPlease check Jenkins logs."
            )
        }
    }
}
