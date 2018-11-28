def remote = [:]
remote.name = 'node'
remote.host = '172.31.21.85'
remote.user = 'coni'
remote.password = '1234'
remote.allowAnyHosts = true

pipeline {
 agent any
 stages {
   stage('SSH Steps') {
     steps {
       withCredentials([usernamePassword(credentialsId: 'webserver_login', passwordVariable:'password', usernameVariable:'userName')]) {
         sshCommand remote: remote, command: 'ssh coni@172.31.21.85'
         sshCommand remote: remote, command: 'mkdir -p /tmp/targetfolder'

         /*writeFile path: '/home', file: 'test', test: 'ls'*\

       }
     }
   }
 }
}
