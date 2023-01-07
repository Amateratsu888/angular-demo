stages {
    stage("clone code") {
        steps{
            git credentialsId:'github-access-token', url: 'https://github.com/Amateratsu888/angular-demo.git', branch:'master'
        }
    }
    stage('build code'){
        steps{
            sh 'npm install'
            sh 'npm run build'
        }
    }
    stage('deploy code'){
        sshagent(['deploy_user']) {
            scp -r /var/lib/jenkins/workspace/angular-demo/dist root@192.168.33.20:/var/www/html
        }
    }
}