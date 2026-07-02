pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shgupta140-max/java-demo-ci.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        always {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
                body: """Hello Team,

The Jenkins build has completed.

Project: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: ${currentBuild.currentResult}

Console Output: ${env.BUILD_URL}console

Regards,
Jenkins CI
""",
                to: 'shgupta140@gmail.com'
            )
        }
    }
}

