pipeline {
    agent any

    stages {
        stage('port-binding') {
            steps {
                sh '''
                    docker rm -f test || true
                    docker run -dp 80:80 --name test httpd
                    
                '''
            }
        }
        
        stage('httpd-container') {
            steps {
                sh '''
                    docker cp index.html test:/usr/local/apache2/htdocs/
                    docker exec test chmod 644 /usr/local/apache2/htdocs/index.html
                '''
            }
        }
    }
}
