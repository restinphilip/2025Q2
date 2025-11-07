pipeline {
    agent any

    stages {
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
