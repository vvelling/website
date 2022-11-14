pipeline {
    agent any
    stages {
        stage('stage I build') {
            steps {
                sh '''
                   sudo su
                   docker build -t assignment:v1 .
		'''
            }
        }
        stage('stage II deploy') {
            when { branch 'master'}
            steps {
                sh '''
                   sudo su
                   docker run -p 82:80 assignment:v1
		'''
            }
        }
    }
}
