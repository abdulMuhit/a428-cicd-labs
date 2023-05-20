
node {
    stage('Send File over SSH') {
                // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        withCredentials([sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'privateKey')]) {
            sh """
                ssh-agent bash -c 'ssh-add \${privateKey}; \
                ssh -i \${privateKey} \${username}@\${server} "mkdir -p /home/test"; \
                scp -i \${privateKey} /README.md \${username}@\${server}:/home/test'
            """
        }
    }
}
