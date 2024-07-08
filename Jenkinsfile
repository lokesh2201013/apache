pipeline {
    agent any
    
    environment {
        GITHUB = 'https://github.com/lokesh2201013/apache/blob/master'
        DESTINATION = '/var/www/html/index.html'
        DESTINATIONCONF = '/etc/httpd'
    }
    
    stages {
        stage('Checkout and Deploy') {
            steps {
                script {
                    // Download index.html from GitHub and save to the destination
                    sh "sudo curl -o ${DESTINATION} ${GITHUB}/index.html"
                   
                    // Download httpd.conf
                    sh "sudo curl -o ${DESTINATIONCONF}/conf/httpd.conf ${GITHUB}/httpd.conf"

                    // Download welcome.conf
                    sh "sudo curl -o ${DESTINATIONCONF}/conf.d/welcome.conf ${GITHUB}/welcome.conf"

                    // Download autoindex.conf
                    sh "sudo curl -o ${DESTINATIONCONF}/conf.d/autoindex.conf ${GITHUB}/autoindex.conf"

                    // Download userdir.conf
                    sh "sudo curl -o ${DESTINATIONCONF}/conf.d/userdir.conf ${GITHUB}/userdir.conf"

                    // Restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                }
            }
        }
    }
}
