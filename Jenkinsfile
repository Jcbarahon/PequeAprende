pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Jcbarahon/PequeAprende.git'
            }
        }

        stage('Setup Flutter') {
            steps {
                bat '''
                echo Configurando Flutter en Windows...
                set PATH=%PATH%;C:\\flutter\\bin
                flutter --version
                '''
            }
        }

        stage('Dependencies') {
            steps {
                bat 'flutter pub get'
            }
        }

        stage('Analyze') {
            steps {
                bat 'flutter analyze'
            }
        }

        stage('Test') {
            steps {
                bat 'flutter test'
            }
        }

        stage('Build') {
            steps {
                bat 'flutter build web'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/web/**'
            }
        }

        // Opcional: Desplegar en Firebase Hosting
        stage('Deploy') {
            steps {
                bat 'firebase deploy --only hosting'
            }
        }
    }
}
