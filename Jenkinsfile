pipeline {
    agent any

    stages {
        stage('Start HTTPD') {
            steps {
                sh '''
                    yum install httpd -y
                    service httpd restart
                '''
            }
        }

        stage('Copy index.html') {
            steps {
                sh '''
                    cp index.html /var/www/html/
                    chmod -R 777 /var/www/html
                '''
            }
        }
    }
}
