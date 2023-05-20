node {
    stage('Send File over SSH') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        sshPublisher(
            continueOnError: false, 
            failOnError: true,
            publishers: [
                sshPublisherDesc(
                configName: "dicoding aws",
                transfers: [sshTransfer(sourceFiles: '/jenkins/**')],
                verbose: true
                )
            ]
        )
    }
}

