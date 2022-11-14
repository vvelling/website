pipeline {
    agent any
    stages {
        stage('stage I build') {
            steps {
                sh '''
                   sudo su
                   sudo docker build -t assignment:v1 .
		'''
            }
        }
        stage('stage II deploy') {
            when { branch 'master'}
            steps {
                sh '''
                   sudo su
                   var='sudo docker ps'
                   if $var | grep cs1
                   then
                       echo "Found a container name 'cs1' running ! removing that container cs1"
                       sudo docker kill cs1
                       sudo docker rm cs1
                   else
                       echo "no running container in the name 'cs1' "
                  fi

                  sudo docker run --name cs1 -p 82:80 assignment:v1 &
                  sleep 10

                  if $var | grep cs1
                  then
                      echo "container running fine"
                      $var
                      exit 0
                  else
                      echo "container not running"
                      exit 1
                  fi

		'''
            }
        }
    }
}
