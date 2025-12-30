pipeline {
    agent any

    stages {
        // Stage 1: Get the code
        stage('Clone Repository') {
            steps {
                echo 'Pulling code from GitHub...'
                checkout scm
            }
        }

        // Stage 2: Get the tools
        stage('Install Dependencies') {
            steps {
                echo 'Installing Python tools...'
                sh 'pip install -r requirements.txt' 
            }
        }

        // Stage 3: Check for bugs
        stage('Run Unit Tests') {
            steps {
                echo 'Testing the application...'
                sh 'pytest test_app.py'
            }
        }

        // Stage 4: Wrap it up
        stage('Build Application') {
            steps {
                echo 'Packaging the application...'
                sh 'tar -czf my-flask-app.tar.gz app.py requirements.txt'
            }
        }

        // Stage 5: Send it out
        stage('Deploy Application') {
            steps {
                echo 'Deploying application...'
                sh 'mkdir -p /tmp/deployment'
                sh 'cp my-flask-app.tar.gz /tmp/deployment'
                echo 'Deployment successful to /tmp/deployment!'
            }
        }
    }
}
