node {
    stage('Copy File') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKey = credentials('dicoding-ssh')
        def remoteDir = '/var/www/html'
        def localFile = '/jenkins/**'
        
        // Copy the file to the remote VM using SSH
        withCredentials([sshUserPrivateKey(credentialsId: privateKey, keyFileVariable: 'privateKey')]) {
            sh "scp -r -i ${privateKey} ${localFile} ${username}@${server}:${remoteDir}"
        }
    }
}
