pipeline {
    agent any

    environment {
        FLUTTER_HOME = 'C:\Users\Administrator\Documents\flutter_windows_3.19.6-stable\flutter'  
        PATH = "$FLUTTER_HOME/bin:$FLUTTER_HOME/bin/cache/dart-sdk/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
               
                git 'git@github.com:Abd-Allah-muhammed-muhammed/gitci.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                  
                    sh 'flutter pub get'
                }
            }
        }

        stage('Build APK') {
            steps {
                script {
                  
                    sh 'flutter build apk --release'
                }
            }
        }

        stage('Archive APK') {
            steps {
               
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
