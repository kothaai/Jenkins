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
            steps {
        script {
          // requires SonarQube Scanner 2.8+
          scannerHome = tool 'SonarQube Scanner 4.6.2.2472'
        }
        withSonarQubeEnv('LocalSonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }

        }
}
}
