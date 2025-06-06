pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Использует настройки SCM из задания
            }
        }
        
        stage('Prepare') {
            steps {
                echo 'Deploying to dev'
            }
        }
        
        stage('Copy Files') {
            steps {
                echo 'Copying files...'
                // Добавьте здесь реальные команды копирования
            }
        }
    }
    
    post {
        always {
            deleteDir()  // Очистка workspace после выполнения
        }
    }
}
