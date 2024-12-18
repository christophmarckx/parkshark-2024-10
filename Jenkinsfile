pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'jdk'
    }

    stages {
        stage('Check Java') {
            steps {
                sh '''
                    echo "JAVA_HOME=$JAVA_HOME"
                    echo "PATH=$PATH"
                    java -version
                    which java
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Test-Stage') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true test'
            }
        }
    }

    post {
        always {
            publishCoverage adapters: [jacocoAdapter('**/target/site/jacoco/jacoco.xml')]
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
