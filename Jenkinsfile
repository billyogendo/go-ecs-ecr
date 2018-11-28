pipeline {
    agent any
    stages {
        stage('clone') {
            when {
                branch 'master'
            }
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
                                        execCommand: 'apt update'
                                        execCommand: 'apt install -y git'
                                        execCommand: 'git clone https://github.com/billyogendo/go-ecs-ecr.git /opt/mike'
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
