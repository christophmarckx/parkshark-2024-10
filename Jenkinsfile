pipeline {
    agent { label 'hoofdnode' }
    stages {
        stage('Check Environment') {
            steps {
                sh '''
                    echo "Hostname: $(hostname)"
                    echo "Working Directory: $(pwd)"
                    echo "Who am I: $(whoami)"
                    echo "Path: $PATH"
                '''
            }
        }
    }
}
