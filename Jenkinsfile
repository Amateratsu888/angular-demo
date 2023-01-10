node {
    stage("clone code") {
            git credentialsId:'github-access-token', url: 'https://github.com/Amateratsu888/angular-demo.git', branch:'master'
    }
    stage('install node_modules'){
            sh 'npm install'
        }
    stage('build code'){
            sh 'npm run build'
        }
    stage('deploy code'){
        sshagent(['deploy_user']) {
            sh 'scp -r -o "PubkeyAuthentication no" /var/lib/jenkins/workspace/angular-demo/dist root@192.168.33.20:/var/www/html'
        }
    }
}