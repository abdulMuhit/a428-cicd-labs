node {
    stage('Copy File') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential
        
        // Copy the file to the remote VM using SSH
        withCredentials([sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'privateKey')]) {
            sh "ls -lah"
            sh "scp -r -i ${privateKey} README.md ${username}@${server}:/var/www/html"
        }
    }
}
