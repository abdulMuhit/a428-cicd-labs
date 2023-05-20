node {
    stage('Copy File') {
        // Define the SSH details for the remote VM
        def server = '13.229.123.107'
        def username = 'ubuntu'
        def privateKeyCredentialId = 'dicoding-ssh' // Replace with the ID of your private key credential
        
        // Copy the file to the remote VM using SSH
        withCredentials([sshUserPrivateKey(credentialsId: privateKeyCredentialId, keyFileVariable: 'privateKey')]) {

            echo "Id ${privateKeyCredentialId}"
            // echo "keyFileVariable ${keyFileVariable}"
            echo "pK ${privateKey}"
            echo "u ${username}"
            echo "s ${server}"
            sh "ls -ld"
            // writeFile file: 'key.pem', text: privateKey
            // sh "cat ./README.md"
            echoe "testfile " > test.text
            sh "cat test.txt"
            sh "ls -lah"
            // sh "scp -r -i ${privateKey} ./README.md ${username}@${server}:/var/www/html"
            // writeFile file: 'key.pem', text: privateKey
            // sh 'chmod 400 key.pem'

            sh "${privateKey} > key.pm"
            sh 'chmod 400 key.pem'
            sh "cat ./key.pem"
            sh "scp -r -i key.pem ./jenkins/** ${username}@${server}:/var/www/html"
        }
    }
}
