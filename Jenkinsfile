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
        }
         stage('--EMail Notification--'){
             steps{
                mail bcc: '', body: '''Hi Welcome to Jenkins Email Alerts
Thanks
Kothaai R''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'poojaravi9810@gmail.com'
             }     
        }
        stage('--Slack Notification--'){
            steps{
                slackSend channel: 'build', color: 'good', message: 'Welcome to jenkins Slack DSL', teamDomain: 'nseitindianbank', tokenCredentialId: 'slack-integration-using-DSL'
    }
}
        stage('--SonarQube Analysis--'){
            steps{
                def mvnHome = tool name: 'maven-3', type: 'maven'
                withSonarQubeEnv('LocalSonarQube')
                sh "${mvnHome}/bin/mvn sonar:sonar"
    }
}
}
}
