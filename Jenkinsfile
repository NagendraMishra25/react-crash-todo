pipeline {
    agent any

    tools {
        nodejs 'NodeJS' // Match the name you configured in Global Tool Configuration cm
    }

    environment {
        GIT_REPO = 'https://github.com/NagendraMishra25/react-crash-todo.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                git branch: 'main', url: env.GIT_REPO
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests defined in package.json
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                // Build the application (if applicable)
                sh 'npm run build'
            }
        }
    }

    post {
        success {
            echo 'Build and test stages completed successfully!'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
