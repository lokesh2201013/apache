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
                    sh " cat ${DESTINATION} > '/var/www/html/index2.html'"
                    sh "sudo truncate --size 0 ${DESTINATION}"
                    
                    // Download index.html from GitHub and save to the destination
                    sh " cat /var/lib/jenkins/workspace/work/index.html > ${DESTINATION}"
                    
                    // Restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                }
            }
        }
    }
}
