pipeline {
    agent any
    stages {
        stage('clone') {
            //when {
                //branch 'master'
            //}
            steps {
                withCredentials([usernamePassword(credentialsId: 'webserver_login', usernameVariable: 'USERNAME', passwordVariable: 'USERPASS')]) {
                    sshPublisher(
                        failOnError: true,
                        continueOnError: false,
                        publishers: [
                            sshPublisherDesc(
                                configName: 'staging',
                                sshCredentials: [
                                    username: "$USERNAME",
                                    encryptedPassphrase: "$USERPASS"
                                ],
                                transfers: [
                                    sshTransfer(
                                        execCommand: 'mkdir tmp/mike_home5' && 'git clone https://billyogendo:@ws#DDD2018@github.com/billyogendo/backend.git /tmp/mike_home5'
                                    )
                                ]
                            )
                        ]
                    )
                }
            }
        
        }
      }
    }
