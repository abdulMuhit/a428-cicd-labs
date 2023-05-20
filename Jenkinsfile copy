node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
                checkout scm
                sh 'npm install'
                sh 'npm run build'
                archiveArtifacts artifacts: 'build/**'
            }
        stage('Test') { 
                sh './jenkins/scripts/test.sh' 
        }
         stage('Manual Approval') {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai cek React App? (Klik "Proceed" untuk lanjut deploy)'
         }
        stage('Deploy') {
               // Define the deployment target server details
                def server = '13.229.123.107'
                def username = 'ubuntu'
                def privateKey = credentials('dicoding-ssh')
                def remoteDir = '/var/www/html'

                // Copy the build artifacts to the server
                withCredentials([sshUserPrivateKey(credentialsId: privateKey, keyFileVariable: 'KEY_FILE')]) {
                    sh "scp -r -i $KEY_FILE build/* ${username}@${server}:${remoteDir}"
                }
                
                // Restart the web server (e.g., Nginx)
                withCredentials([sshUserPrivateKey(credentialsId: privateKey, keyFileVariable: 'KEY_FILE')]) {
                    sh "ssh -i $KEY_FILE ${username}@${server} 'sudo service nginx restart'"
                }

                echo 'Now...'
                echo 'Visit http://18.141.12.109 to see your Node.js/React application in action.'
                sh './jenkins/scripts/kill.sh'
        }
    }
}