pipeline {
  environment {
    USER = credentials("webserver_login")
  }
  
  agent any
  
  stages {
    stage("testing") {
      steps {
        sh 'echo "user is $USER"'
        
        //write to file
        dir("combined") {
          sh 'echo $USER >> /tmp/mikes.txt'
        }
      }
    }
  }
}
