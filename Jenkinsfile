pipeline {
   agent any
   stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'laravel']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '609d39e4-f3ae-40b4-b26e-e4c5113508f4', url: 'https://github.com/gopireddy1135/semaphore-demo-php-laravel.git']]])
                sh "ls"
                sh "sudo apt-get install php"
                sh "sudo apt update"
                sh "sudo apt install curl"
                sh "php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');""
                sh "php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;""
                sh "php composer-setup.php"
                sh "php -r "unlink('composer-setup.php');""
                sh "sudo mv composer.phar /usr/local/bin/composer"
                sh "composer"
            }
        }     
    }
}
