pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies"
                sh 'python3 -m pip install flask numpy scikit-learn'
            }
        }

        stage('Run ML Application') {
            steps {
                echo "Running ML application"
                sh 'python3 ml_app.py &'
            }
        }

        stage('Test API') {
            steps {
                echo "Testing API"
                sh 'sleep 5'
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
