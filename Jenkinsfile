pipeline {
    agent any
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
                docker stop myapp && echo "Stopped taks1£ || echo "task1 not running"
                docker rm myapp && echo "removed taks1£ || echo "task1 does not exist"
                docker run -d -p 80:5500 --name myapp pixcs13/task1jenk
                '''
            }

        }

    }

}