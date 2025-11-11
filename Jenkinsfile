pipeline {
    agent any

    stages {
         stage('volume') {
            steps {
                sh '''
                    cp index.html /mnt
                    chmod -R 744 /mnt*
                '''
            }
        }
        stage('port-binding bind-mount') {
            steps {
                sh '''
                    docker rm -f test || true
                     docker run -dp 90:80 -v /mnt:/usr/local/apache2/htdocs/ --name test httpd
                     docker exec test chmod 644 /usr/local/apache2/htdocs/index.html
                    
                '''
            }
        }
    }
}
