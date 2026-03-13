pipeline {
    agent any

    stages {

        stage('Setup Python Environment') {
            steps {
                echo "Creating virtual environment"
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install flask numpy scikit-learn
                '''
            }
        }

        stage('Run ML Application') {
            steps {
                echo "Running ML application"
                sh '''
                . venv/bin/activate
                python ml_app.py &
                '''
            }
        }

        stage('Test API') {
            steps {
                echo "Testing API endpoint"
                sh '''
                sleep 5
                curl http://localhost:5002/ml/health
                '''
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
