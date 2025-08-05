pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/davidmoi2135/testnextjsproject.git'
            }
        }

        stage('Install Node.js') {
            steps {
                // Cài đặt Node.js nếu Jenkins bạn có plugin Node.js
                // Nếu chưa, bạn có thể cài trực tiếp trên máy
                sh 'node -v || curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash - && sudo apt-get install -y nodejs'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Run (optional)') {
            steps {
                // Nếu bạn muốn test thử chạy server, bật port (ví dụ cho QA)
                sh 'nohup npm run start &'
            }
        }
    }
}