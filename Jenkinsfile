pipeline {
    agent any
    
    environment {
        GITHUB = 'https://github.com/lokesh2201013/apache'
        GITHUBFILE = 'index.html'
        DESTINATION = '/var/www/html/index.html'
        DESTINATIONCONF='/etc/httpd'
    }
    
    stages {
        stage('Checkout and Deploy') {
            steps {
                script {
                    // Clear the contents of the destination file
                    sh "sudo truncate --size 0 ${DESTINATION}"
                    
                    // Download index.html from GitHub and save to the destination
                    sh " cat https://github.com/lokesh2201013/apache/index.html > ${DESTINATION}"
                    
                    sh "sudo truncate --size 0 ${DESTINATIONCONF/conf/httpd.conf}"

                    sh "cat https://github.com/lokesh2201013/apache/httpd.conf > ${DESTINATIONCONF/conf/httpd.conf}"
                     
                     sh "sudo truncate --size 0 ${DESTINATIONCONF/conf.d/welcome.conf}"

                    sh "cat https://github.com/lokesh2201013/apache/welcome.conf > ${DESTINATIONCONF/conf.d/welcome.conf}"

                    sh "sudo truncate --size 0 ${DESTINATIONCONF/conf.d/autoindex.conf}"

                    sh "cat https://github.com/lokesh2201013/apache/autoindex.conf > ${DESTINATIONCONF/conf.d/autoindex.conf}"

                    sh "sudo truncate --size 0 ${DESTINATIONCONF/conf.d/userdir.conf}"

                    sh "cat https://github.com/lokesh2201013/apache/userdir.conf > ${DESTINATIONCONF/conf.d/userdir.conf}"

                    // Restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                   
                }
            }
        }
    }
}
