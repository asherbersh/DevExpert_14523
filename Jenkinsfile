pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                script {
                    properties([pipelineTriggers([pollSCM('* * * * *')])])
                }
                git 'https://github.com/asherbersh/DevExpert_14523.git'
            }
        }
        stage('run python') {
            steps {
                script {
                    if (checkOs() == 'Windows') {
                        bat 'python first.py'
                    } else {
                        sh 'python second.py'
                    }
                }
            }
        }
    }
}

def checkOs(){
    if (isUnix()) {
        def uname = sh script: 'uname', returnStdout: true
        if (uname.startsWith("Darwin")) {
            return "Macos"
        }
        else {
            return "Linux"
        }
    }
    else {
        return "Windows"
    }
}