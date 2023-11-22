pipeline {
    agent any
    environment {
        YOUR_NAME = credentials("YOUR_NAME")
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                docker build -t pixcs13/task1jenk .
                '''
            }

        }
        stage('Push') {
            steps {
                sh '''
                docker push pixcs13/task1jenk
                '''
            }

        }
        stage('Deploy') {
            steps {
                sh '''
                kubectl apply -f .
                '''
            }

        }

    }

}