pipeline {
    agent any
    parameters {
        choice(name: 'ENV', choices: ['dev', 'prod'], description: 'Выберите окружение')
    }
    stages {
        stage('Prepare') {
            steps {
                echo "Deploying to ${params.ENV}"
                cleanWs() // Очистка рабочей директории
            }
        }
        stage('Copy Files') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'TargetServer', // Имя из настроек SSH
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*', // Копировать все файлы
                                    removePrefix: '', // Не обрезать префикс пути
                                    remoteDirectory: "${params.ENV}", // Папка на целевой VM
                                    execCommand: "echo 'Деплой в ${params.ENV} завершен!'"
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}
