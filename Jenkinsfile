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
            sshPublisher(
                continueOnError: false, 
                failOnError: true,
                publishers: [
                    sshPublisherDesc(
                    configName: "dicoding aws",
                    transfers: [ 
                        sshTransfer(execCommand: "echo 'logged'"),
                        sshTransfer(flatten: false,
                        remoteDirectory: '../var/www/html',
                        sourceFiles: 'build/**'
                        )
                    ],
                    verbose: true
                    )
                ]
            )

        }
    }
}