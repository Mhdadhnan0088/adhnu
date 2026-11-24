
pipeline {
    agent none

    stages {
        stage('build') {
            agent {
                label 'build-node'
            }

            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/Mhdadhnan0088/adhnu.git
                    ls -la
                '''

                stash name: 'webpage', includes: 'adhnu/**'
            }
        }

        stage('deploy') {
            agent {
                label 'build-node'
            }

            steps {
                deleteDir()

                unstash 'webpage'

                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r adhnu/* /var/www/html/
                    ls -la /var/www/html/
                '''
            }
        }
    }
}
