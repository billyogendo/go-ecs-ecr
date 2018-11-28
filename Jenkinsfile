pipeline {
	environment {
		USER = credentials("webserver_login")
	}
    agent none
    stages {
            stage('test') {
            agent any
            steps {
                sshagent (credentials: ['$USER']) {
    sh '''
echo '1234' | ssh -vv coni@34.245.222.45 echo testing connection || true
ssh-add -L
echo done running remote server test
'''

  }
            }
        }


}
}
