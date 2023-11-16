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
                docker build -t pixcs13/task1-nginx nginx
                '''
            }

        }
        stage('Push') {
            steps {
                sh '''
                docker push pixcs13/task1jenk
                docker push pixcs13/task1-nginx
                '''
            }

        }
        stage('Deploy') {
            steps {
                sh '''
                ssh jenkins@maria-deploy <<EOF
                export YOUR_NAME=${YOUR_NAME}
                docker network rm task1-net && echo "removed network" || echo "network already removed"
                docker network create task1-net
                docker stop nginx && echo "Stopped nginx" || echo "nginx not running"
                docker rm nginx && echo "removed nginx" || echo "nginx does not exist"
                docker stop flask-app && echo "Stopped flask-app" || echo "flask-app not running"
                docker rm flask-app && echo "removed flask-app" || echo "flask-app does not exist"
                docker run -d --name flask-app --network task1-net -e YOUR_NAME=${YOUR_NAME} pixcs13/task1jenk
                docker run -d --name nginx --network task1-net -p 80:80 pixcs13/task1-nginx
                '''
            }

        }

    }

}