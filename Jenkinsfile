pipeline {
  environment {
    FOO = credentials("webserver_login")
  }
  
  agent any
  
  stages {
    stage("foo") {
      steps {
        sh 'echo "FOO is $FOO"'
        
        //write to file
        dir("combined") {
          sh 'echo $FOO >> /tmp/mike.txt'
        }
      }
    }
  }
}
