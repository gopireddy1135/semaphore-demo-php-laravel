pipeline {
   agent any
   stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'laravel']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '609d39e4-f3ae-40b4-b26e-e4c5113508f4', url: 'https://github.com/gopireddy1135/semaphore-demo-php-laravel.git']]])
                sh "sudo apt-get install php"
                sh "sudo apt update"
                sh "sudo apt install curl"
                sh "curl -sS https://getcomposer.org/installer | php"
                sh "chmod +x composer.phar"
                sh "sudo mv composer.phar /usr/local/bin/composer"
                sh "composer -V"
                sh "sudo apt install npm"
                sh "npm install -y"
                sh "sh php artisan"
                sh "composer create-project laravel/laravel testlaravelproject"
                sh "cd testlaravelproject"
                sh "composer install"
            }
        }     
    }
}
   
   

   
   
   
