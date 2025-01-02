pipeline {
    agent any
    tools {
        nodejs 'nodejs'
    }
    environment {
        SONARQUBE_URL = 'http://localhost:9099'
        SONARQUBE_TOKEN = 'sqp_62ac22e3820cec471baeda6663beda1989078d30'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/saitejavellanki/Worldline.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    echo "Skipping tests as none are defined yet."
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    bat """
                    sonar-scanner -Dsonar.projectKey=backend_project -Dsonar.sources=src -Dsonar.host.url=http://localhost:9099 -Dsonar.login=sqp_62ac22e3820cec471baeda6663beda1989078d30
                    """
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        failure {
            echo 'Build failed. Check logs for details.'
        }
    }
}
