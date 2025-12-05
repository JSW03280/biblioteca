pipeline {
    agent any

    tools {
        jdk 'jdk-17'
        maven 'Maven3.9.11'
    }

    environment {
        VERSION_BACK = "2.0.1"
    }

    stages {
        stage ('Show messages') {
            steps {
                bat "echo 'Primer stage del pipeline'"
                bat "echo 'A continuacion hacemos checkout del proyecto'"
            }
        }

        stage ('Checkout del proyecto') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/JSW03280/biblioteca.git'
            }
        }

        stage ('Comandos Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage ('Crear directorio') {
            steps {
                bat 'IF NOT EXIST "v%VERSION_BACK%" mkdir "v%VERSION_BACK%"'
            }
        }

        stage ('Mover .jar') {
            steps {
                bat 'xcopy /Y ".\\target\\*.jar" ".\\v%VERSION_BACK%"'
            }

            post {
                success {
                    bat 'echo ".jar copiados"'
                }

                failure {
                    bat 'echo "Error al copiar los ficheros"'
                }

                always {
                    bat 'echo "Eta vaina ta plende"'
                }
            }
        }
    }
}