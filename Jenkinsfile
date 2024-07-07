pipeline {
    agent any
    
    environment {
        GITHUB = 'https://github.com/lokesh2201013/apache'
        GITHUBFILE = 'index.html'
        DEST = '/var/www/html/index.html'
    }
    
    stages {
        stage('Updateing') {
            steps {
                script {
                    // backup for the orignal file
                    sh " sudo cat ${DEST} > '/var/www/html/index2.html'"
                    // delete all content of index.html
                    sh "sudo truncate --size 0 ${DEST}"
                    // take index.html from jenkins workspace
                    sh " cat /var/lib/jenkins/workspace/work/index.html > ${DEST}"
                    // restart httpd service
                    sh 'sudo systemctl restart httpd.service'
                }
            }
        }
    }
}
