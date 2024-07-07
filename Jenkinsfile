pipeline {
    agent any
    
    environment {
        GITHUB = 'https://github.com/lokesh2201013/apache'
        GITHUBFILE = 'index.html'
        DESTINATION = '/var/www/html/index.html'
    }
    
    stages {
        stage('Checkout and Deploy') {
            steps {
                script {
                    // Clear the contents of the destination file
                    sh "sudo truncate --size 0 ${DESTINATION}"
                    
                    // Download index.html from GitHub and save to the destination
                    sh " curl -s ${GITHUB}/${GITHUBFILE} > ${DESTINATION}"
                    
                    // Restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                    
                    // Open localhost:80 in Firefox
                    sh 'firefox http://localhost:80'
                }
            }
        }
    }
}
