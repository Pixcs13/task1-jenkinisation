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
                docker stop task1_m && echo "Stopped taks1£ || echo "task1 not running"
                docker rm task1_m && echo "removed taks1£ || echo "task1 does not exist"
                docker run -d -p 80:5500 --name task1_m pixcs13/task1jenk
                '''
            }

        }

    }

}