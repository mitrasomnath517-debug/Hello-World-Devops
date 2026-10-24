
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Checking website..."
                    test -f index.html
                    grep -qi "<html" index.html
                    echo "HTML check passed"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Deploying website..."
                    install -m 644 index.html /var/www/html/index.html
                    echo "Deployment completed"
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                    curl --fail http://localhost/
                '''
            }
        }
    }
}
