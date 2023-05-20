pipeline {
    agent any
    stages {
        stage('Send File over SSH') {
            steps {
                sshagent(['dicoding-ssh']) {
                    script {
                        def remoteServer = '13.229.123.107'
                        def remoteUser = 'ubuntu'
                        def remoteFilePath = '/var/www/html'
                        def localFilePath = '/jenkins/**'

                        // Copy the file to the remote server
                        // sshCommand remote: remoteServer, user: remoteUser, command: "mkdir -p ${remoteFilePath}"
                        sshCommand remote: remoteServer, user: remoteUser, command: "scp ${localFilePath} ${remoteUser}@${remoteServer}:${remoteFilePath}"
                    }
                }
            }
        }
    }
}
