pipeline {
    agent any

    environment {
        FLUTTER_HOME = 'C:\Users\Administrator\Documents\flutter_windows_3.19.6-stable\flutter'  // تأكد من تعديل المسار إلى موقع Flutter على الخادم
        PATH = "$FLUTTER_HOME/bin:$FLUTTER_HOME/bin/cache/dart-sdk/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                // سحب الكود من GitHub
                git 'git@github.com:Abd-Allah-muhammed-muhammed/gitci.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // تثبيت الاعتمادات الخاصة بـ Flutter
                    sh 'flutter pub get'
                }
            }
        }

        stage('Build APK') {
            steps {
                script {
                    // بناء APK باستخدام Flutter
                    sh 'flutter build apk --release'
                }
            }
        }

        stage('Archive APK') {
            steps {
                // أرشفة الـ APK الناتج
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
