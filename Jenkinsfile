pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    // Fetch the code from Git repository
                    checkout([$class: 'GitSCM', 
                              branches: [[name: '*/main']],
                              userRemoteConfigs: [[url: 'https://github.com/saitejavellanki/Worldline.git']]])
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install project dependencies
                    bat 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    // Run tests if defined in the package.json scripts section
                    bat 'npm test' // Change this if your test command is different
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    // Start the application
                    bat 'npm start'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline execution completed successfully!'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
