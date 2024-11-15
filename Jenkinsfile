pipeline {
    agent any

    environment {
        FLUTTER_HOME = 'C:\\Users\\Administrator\\Documents\\flutter_windows_3.19.6-stable\\flutter'  
        ANDROID_HOME = 'C:\\Users\\Administrator\\AppData\\Local\\Android\\Sdk' 
        PATH = "$FLUTTER_HOME\\bin;$FLUTTER_HOME\\bin\\cache\\dart-sdk\\bin;$ANDROID_HOME\\platform-tools;$ANDROID_HOME\\tools;$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                // Cloning the repository from GitHub
                git 'https://github.com/Abd-Allah-muhammed-muhammed/ci_cd_github_actions.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Flutter dependencies
                    bat 'flutter pub get'  // Use bat for Windows
                }
            }
        }

        stage('Build APK') {
            steps {
                script {
                    // Build APK
                    bat 'flutter build apk --release'  // Use bat for Windows
                }
            }
        }

        stage('Archive APK') {
            steps {
                // Archive the generated APK file
                archiveArtifacts allowEmptyArchive: true, artifacts: '**/build/app/outputs/flutter-apk/app-release.apk', onlyIfSuccessful: true
            }
        }
    }

    post {
        success {
            echo 'تم بناء APK بنجاح!'
        }
        failure {
            echo 'حدث خطأ أثناء البناء.'
        }
    }
}
