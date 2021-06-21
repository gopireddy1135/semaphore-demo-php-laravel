pipeline {
  agent any
 stages {
    stage('Build') {
      steps {
         checkout([$class: 'GitSCM', branches: [[name: 'laravel']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '609d39e4-f3ae-40b4-b26e-e4c5113508f4', url: 'https://github.com/gopireddy1135/semaphore-demo-php-laravel.git']]])
                sh "sudo apt install php7.4"
                sh "sudo apt install php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl -y"
                sh "sudo apt install curl"
                sh "curl -sS https://getcomposer.org/installer | php"
                sh "chmod +x composer.phar"
                sh "sudo mv composer.phar /usr/local/bin/composer"
                sh "composer -V"
                sh "sudo apt install npm"
                sh "cd /var/lib/jenkins/workspace && npm install"
                sh "pwd"
                sh "composer install"
                sh "php artisan migrate:rollback"
                sh "sudo apt-get install php-sqlite3 -y"
                sh "wget https://phar.phpunit.de/phpunit-9.5.phar"
                sh "sudo chmod +x phpunit-9.5.phar"
                sh "php phpunit-9.5.phar --version"
                sh "./phpunit-9.5.phar --version"
                sh "phpunit UnitTest"
                
          }
       }
        stage('Test') {
          steps {
                sh "vendor/bin/phpunit"
                sh "vendor/bin/phpunit --testdox tests"
          }
       }
        stage ("code quality") {
          steps {
                sh "phpunit --log-junit 'reports/unitreport.xml' --coverage-html 'reports/coverage' --coverage-clover 'reports/coverage/coverage.xml' tests"
          }
       }        
   }      
}

    
