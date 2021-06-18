pipeline {
   agent any
   stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/branchname']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gopireddy1135', url: 'https://github.com/gopireddy1135/semaphore-demo-php-laravel.git
']]])
                sh "ls -lart ./*"
            }
        }     
    }
}
