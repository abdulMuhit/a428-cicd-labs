node {
    stage('Send File over SSH') {
        // Define the SSH details for the remote server
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        // SSH connection and file transfer
        sshagent(credentials: [sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'privateKey')]) {
            sh """
                scp -i \${privateKey} /README.md \${username}@\${server}:/var/www/html/
            """
        }
    }
}
