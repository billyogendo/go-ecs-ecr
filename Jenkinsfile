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
                                        execCommand: 'mkdir tmp/mike_home2' && 'git clone https://github.com/billyogendo/amazon-ecs-plugin.git'
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
