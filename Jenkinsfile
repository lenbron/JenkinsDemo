pipeline {
    agent any

    stages {
        stage('Pull code') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '016aa6bb-c4af-4cf5-a2b0-e5d08205b71c', url: 'git@github.com:lenbron/JenkinsDemo.git']])
            }
        }
        stage('Build project') {
            steps {
                sh '''lmgrd -c /home/synopsys/scl/2018.06/admin/license/Synopsys.dat
                        vcs -full64 -cpp g++-4.8 -cc gcc-4.8 -LDFLAGS -Wl,--no-as-needed demo1.v -debug_all
                        ./simv'''
            }
        }
        stage('Push project') {
            steps {
                echo 'Push project'
            }
        }
    }
}
