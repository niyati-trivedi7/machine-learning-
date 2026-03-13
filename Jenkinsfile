pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies"
                sh 'pip install flask numpy scikit-learn'
            }
        }

        stage('Run ML Application') {
            steps {
                echo "Running ML app"
                sh 'python ml_app.py &'
            }
        }

        stage('Test API') {
            steps {
                echo "Testing API"
                sh 'curl http://localhost:5002/ml/health'
            }
        }

    }

    post {
        success {
            echo "Pipeline executed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
