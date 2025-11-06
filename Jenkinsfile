pipeline {
    agent any

    stages {
        stage('start_docker') {
            steps {
                sh '''
                    yum install docker -y
                    service docker start
                '''
            }
        }

        stage('port-binding') {
            steps {
                sh '''
                    docker run -dp 80:80 --name test httpd
                    
                '''
            }
        }
        
        stage('httpd-container') {
            steps {
                sh '''
                    docker cp index.html test:/usr/local/apache2/htdocs/
                '''
            }
        }
    }
}
