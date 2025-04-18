pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/yourusername/your-python-repo.git'
            }
        }
        stage('Setup Python') {
            steps {
                bat '''
                python -m venv venv
                venv\\Scripts\\activate
                pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                bat '''
                venv\\Scripts\\activate
                pytest > result.txt
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'result.txt', onlyIfSuccessful: true
        }
    }
}
