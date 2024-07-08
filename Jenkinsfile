pipeline {
    agent any
    
    environment {
        GITHUB = 'https://raw.githubusercontent.com/lokesh2201013/apache/main'
        DESTINATION = '/var/www/html/index.html'
        DESTINATIONCONF = '/etc/httpd'
    }
    
    stages {
        stage('Updateing') {
            steps {
                script {
                    // Download index.html from GitHub and save to the destination
                    sh "curl -o ${DESTINATION} ${GITHUB}/index.html"
                    
                    // Ensure the httpd configuration directories exist
                    sh "sudo mkdir -p ${DESTINATIONCONF}/conf"
                    sh "sudo mkdir -p ${DESTINATIONCONF}/conf.d"

                    // Download httpd.conf
                    sh "curl -o ${DESTINATIONCONF}/conf/httpd.conf ${GITHUB}/httpd.conf"

                    // Download welcome.conf
                    sh "curl -o ${DESTINATIONCONF}/conf.d/welcome.conf ${GITHUB}/welcome.conf"

                    // Download autoindex.conf
                    sh "curl -o ${DESTINATIONCONF}/conf.d/autoindex.conf ${GITHUB}/autoindex.conf"

                    // Download userdir.conf
                    sh "curl -o ${DESTINATIONCONF}/conf.d/userdir.conf ${GITHUB}/userdir.conf"

                    // Restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                }
            }
        }
    }
}
