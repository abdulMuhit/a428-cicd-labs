node {
    stage('Send File over SSH') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        withCredentials([sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'privateKey')]) {
            withEnv(['PRIVATE_KEY=$privateKey']) {
                sh 'ssh-agent bash -c "ssh-add $PRIVATE_KEY; scp -i $PRIVATE_KEY /README.md $username@$server:/var/www/html"'
            }
        }
    }
}

