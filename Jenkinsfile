node {
    stage('Send File over SSH') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential

        cleanWs()
        sh "echo 'hello' >> file1.txt"
        sh "echo 'hello' >> file2.txt"
        // sh "zip -r oneFile.zip file1.txt file2.txt"
            
        echo 'Local files.....'       
        sh 'ls -l'

        //  unzip -o -d ./ oneFile.zip
        command='''
            ls -l
            date
            cat /etc/os-release
        '''

        // Copy file to remote server 
        sshPublisher(publishers: [sshPublisherDesc(configName: 'dicoding aws',
        transfers: [ sshTransfer(flatten: false,
                        remoteDirectory: './',
                        sourceFiles: 'file1.txt'
        )])
        ])
        
        // Execute commands
        sshPublisher(publishers: [sshPublisherDesc(configName: 'dicoding aws',
        transfers: [ sshTransfer(execCommand: command)])])

        sshPublisher(
            continueOnError: false, 
            failOnError: true,
            publishers: [
                sshPublisherDesc(
                configName: "dicoding aws",
                transfers: [ 
                    sshTransfer(execCommand: "echo 'logged'")],
                verbose: true
                )
            ]
        )
    }
}

