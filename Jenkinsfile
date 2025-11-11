pipeline {
    agent any

    stages {
         stage('volume') {
            steps {
                sh '''
                    docker volume create volume || true
                    cp index.html /var/lib/docker/volumes/volume/_data
                '''
            }
        }
        stage('port-binding bind-mount') {
            steps {
                sh '''
                    docker rm -f test || true
                     docker run -dp 90:80 -v volume:/usr/local/apache2/htdocs/ --name test httpd
                     docker exec test chmod 644 /usr/local/apache2/htdocs/index.html
                    
                '''
            }
        }
    }
}
