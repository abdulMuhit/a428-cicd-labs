
node {
    stage('Send File over SSH') {
                // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        def path = './dicoding-abdul.pem'
        
        sh "ssh -v -i ${path} ubuntu@13.229.123.107 "echo 'SSH connection successful'""
    }
}
