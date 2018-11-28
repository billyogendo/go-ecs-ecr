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
                                        execCommand: 'mkdir tmp/mike_home4' && ' git branch: 'master', credentialsId: 'githubcredentials', url: 'https://github.com/billyogendo/backend.git /tmp/mike_home4'
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
