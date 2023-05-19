node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
                sh 'npm install'
            }
        stage('Test') { 
                sh './jenkins/scripts/test.sh' 
        }
         stage('Manual Approval') {
                sh './jenkins/scripts/deliver.sh'
                archiveArtifacts artifacts: 'build/**'
                input message: 'Sudah selesai cek React App? (Klik "Proceed" untuk lanjut deploy)'
                sh './jenkins/scripts/kill.sh'
         }
        stage('Deploy') {
               // Define the deployment target server details
                def server = '13.229.123.107'
                def username = 'ubuntu'
                def privateKey = credentials('dicoding-ssh')
                def remoteDir = '/var/www/html'
                
                // Copy the build artifacts to the server
                sshagent(credentials: [privateKey]) {
                    sh "pwd"
                    sh "scp -r build/* ${username}@${server}:${remoteDir}"
                }
                
                // Restart the web server (e.g., Nginx)
                sshagent(credentials: [privateKey]) {
                    sh "ssh ${username}@${server} 'sudo service nginx restart'"
                }

                echo 'Now...'
                echo 'Visit http://18.141.12.109 to see your Node.js/React application in action.'
        }
    }
}