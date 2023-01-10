node {
    stage("clone code") {
            git credentialsId:'github-access-token', url: 'https://github.com/Amateratsu888/angular-demo.git', branch:'master'
    }
    stage('install node_modules'){

            sh 'npm install'
            sh 'su vagrant'
        }
    stage('build code'){
            sh 'whoami'
            sh 'npm run build'
        }
    stage('deploy code'){
        sshagent(['deploy_user']) {
            sh 'scp -o "PubkeyAuthentication no" -r  /var/lib/jenkins/workspace/angular-demo/dist root@192.168.33.20:/var/www/html'
        }
    }
}