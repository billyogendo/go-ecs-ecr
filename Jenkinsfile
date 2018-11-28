pipeline {
    agent any
    stages {
        stage('DeployToStaging') {
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
                                        execCommand: 'git branch: 'master', credentialsId: 'githubcredentials', url: "https://github.com/billyogendo/go-ecs-ecr.git"'
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
