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
             sh 'scp  -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/angular-demo-pipeline/default vagrant@192.168.33.20:/etc/nginx/sites-available/default'
             sh 'scp -r -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/angular-demo-pipeline/dist vagrant@192.168.33.20:/var/www/html'
         }
 }
}
