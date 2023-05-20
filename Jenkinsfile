node {
    stage('Send File over SSH') {
        // Define the SSH details for the remote server
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential


        withCredentials([sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'KEY_FILE')]) {
                    sh "ssh -i $KEY_FILE ${username}@${server} 'echo connected established ready ok'"
        }
    }
}


