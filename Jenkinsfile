pipeline {
    agent any

    tools {
        jdk 'jdk-17'
        maven 'Maven3.9.11'
    }

    stages {
        stage('Show messages') {
            steps {
                echo 'Primer stage del pipeline'
                echo 'A continuacion hacemos checkout del proyecto'
            }
        }

        stage ('Checkout del proyecto') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/JSW03280/biblioteca.git'
            }
        }

        stage ('Maven clean') {
            steps {
                bat 'mvn clean'
            }
        }
    }
}