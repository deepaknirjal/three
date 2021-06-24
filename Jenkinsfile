pipeline {
    agent none

    stages {

        stage('clone') {
            agent {label 'node1'}
            steps {
                sh '''#!/bin/bash
                cd /var/www/html
                if [ ! -x "/usr/bin/git" ] && [! -d "/var/www/html/three" ]
                then
                    apt install git -y
                    git clone -b 2nd_branch https://github.com/deepaknirjal/three.git/
                else
                        rm -rf /var/www/html/three
                        git clone -b 2nd_branch https://github.com/deepaknirjal/three.git/
                fi
                '''
            }
        }
        stage('restart service'){
            agent {label 'node1'}
            steps{
                sh '''#!/bin/bash
                service apache2 restart
                '''
            }
        }
    }
}

