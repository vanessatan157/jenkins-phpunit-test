pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Run composer install using Windows batch command
                bat 'composer install'
            }
        }
        stage('Test') {
            steps {
                // Run PHPUnit tests using Windows batch command
                bat './vendor/bin/phpunit --log-junit logs\\unitreport.xml -c tests\\phpunit.xml tests'
            }
        }
    }
    post {
        always {
            // Publish the test results
            junit testResults: 'logs\\unitreport.xml'
        }
    }
}