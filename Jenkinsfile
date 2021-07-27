pipeline {
    agent any
    stages {
        stage('---clean---') {
            steps {
                sh "mvn clean"
            }
        }
        stage('--test--') {
            steps {
                sh "mvn test"
            }
        }
        stage('--package--') {
            steps {
                sh "mvn package"
            }
            stage('--EMail Notification--'){
                mail bcc: '', body: '''Hi Welcome to Jenkins Email Alerts
Thanks
Kothaai R''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'poojaravi9810@gmail.com'
                
        }
    }
}
