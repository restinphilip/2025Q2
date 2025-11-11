pipeline {
    agent any

    stages {
         stage('volume') {
            steps {
                sh '''
                     docker build -t myhttpd:1.0 .
                '''
            }
        }
        stage('port-binding bind-mount') {
            steps {
                sh '''
                    docker rm -f test || true
                     docker run -dp 90:80 --name test myhttpd:1.0
                    
                '''
            }
        }
    }
}
