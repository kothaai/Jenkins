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
       /* stage('--EMail Notification--'){
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
}*/
     stage('sonar-scanner') {
	     steps {
		     script {
			     def sonarqubeScannerHome = tool name: 'SonarQubeRunner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
			     withCredentials([string(credentialsId: 'sonar', variable: 'sonarLogin')]) {
			     sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://192.168.1.24:9000 -Dsonar.login=${sonarLogin} -Dsonar.projectName=gs-gradle -Dsonar.projectVersion=${env.BUILD_NUMBER} -Dsonar.projectKey=SonarTest -Dsonar.projectName=SonarTest -Dsonar.projectVersion=1.0 -Dsonar.sources=/var/lib/jenkins/workspace/$JOB_NAME -Dsonar.sourceEncoding=UTF-8 -Dsonar.host.url=http://jenkins.nseit.com:9000 -Dsonar.sources=src/main/java -Dsonar.language=java -Dsonar.java.binaries=target/classes"
			}
		     }
	     }
    }
}
}
