node {
    stage('Send File over SSH') {
        withCredentials([sshUserPrivateKey(credentialsId: 'dicoding-ssh', keyFileVariable: 'privateKey')]) {
            sshagent(['dicoding-ssh']) {
                sh 'ssh ubuntu@13.229.123.107 "mkdir -p /home/test"'
                sh 'scp -i $privateKey /README.md ubuntu@13.229.123.107:/home/test'
            }
        }
    }
}
