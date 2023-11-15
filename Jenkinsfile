pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                docker build -t pixcs13/myapp .
                '''
            }

        }
        stage('Push') {
            steps {
                sh '''
                docker push pixcs13/myapp
                '''
            }

        }
        stage('Deploy') {
            steps {
                sh '''

                docker run -d -p 80:5500 --name myapp pixcs13/myapp
                '''
            }

        }

    }

}