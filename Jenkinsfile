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
                                        execCommand:'git clone git branch: 'master', credentialsId: 'mycredentials', url: 'https://github.com/billyogendo/go-ecs-ecr.git''
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
