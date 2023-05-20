node {
    stage('Send File over SSH') {
        withCredentials([sshUserPrivateKey(credentialsId: 'dicoding-ssh', keyFileVariable: 'privateKey')]) {
            sh '''
                ssh-agent bash -c "ssh-add ${privateKey}; \
                ssh ubuntu@13.229.123.107 'mkdir -p /home/test'; \
                scp -i ${privateKey} /README.md ubuntu@13.229.123.107:/home/test"
            '''
        }
    }
}
