pipeline {
    agent any

    environment {
        FLUTTER_HOME = 'C:\\src\\flutter'
        PATH = "${FLUTTER_HOME}\\bin;${env.PATH}"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git'
            }
        }

        stage('Flutter Version') {
            steps {
                bat 'flutter --version'
            }
        }

        stage('Install Dependencies') {
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

        stage('Build APK') {
            steps {
                bat 'flutter build apk --release'
            }
        }
    }

    post {
        success {
            echo 'Flutter CI/CD pipeline completed successfully!'
        }

        failure {
            echo 'Flutter CI/CD pipeline failed!'
        }

        always {
            archiveArtifacts artifacts: 'build\\app\\outputs\\flutter-apk\\app-release.apk',
                             allowEmptyArchive: true
        }
    }
}