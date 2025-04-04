pipeline {
    agent { label 'atharva' }  // Specify the agent named 'atharva'
    stages {
        stage('Checkout Repository') {
            steps {
                script {
                    echo 'Cloning the repository...'
                    // Clone the repository
                    git url: "https://github.com/atharva0608/two-tier-flask-app.git", branch: 'master'
                }
            }
        }

        stage('Build and Deploy Docker Containers') {
            steps {
                script {
                    echo 'Running docker compose up with rebuild...'
                    // Navigate to the project directory and run docker-compose with --build flag
                    dir('two-tier-flask-app') {
                        sh 'docker compose down && docker compose up -d --build'
                    }
                }
            }
        }

        stage('Check Docker Status') {
            steps {
                script {
                    echo 'Checking Docker container status...'
                    // Check if containers are running
                    sh 'docker ps'
                }
            }
        }
    }
}
