pipeline {
    agent any

    stages {
        stage('port-binding') {
            steps {
                sh '''
                    docker rm -f test1 || true
                    docker run -dp 9090:80 --name test1 httpd
                    
                '''
            }
        }
        
        stage('httpd-container') {
            steps {
                sh '''
                    docker cp index.html test1:/usr/local/apache2/htdocs/
                    docker exec test1 chmod 644 /usr/local/apache2/htdocs/index.html
                '''
            }
        }
    }
}
