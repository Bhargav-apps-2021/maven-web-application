node{
def mavenHome = tool name: "maven3.8.4"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

stage('CheckoutCode'){
git branch: 'development', credentialsId: '85c367ca-b474-4595-8659-8ba25a1e5dd3', url: 'https://github.com/Bhargav-apps-2021/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecutionSonarQubeReport'){
sh "${mavenHome}/bin/mvn sonar:sonar"
}

stage('Upload artifacts into NEXSUS'){
sh "${mavenHome}/bin/mvn deploy"
}

stage('DeployAppintoTomcatServer'){

sshagent(['3c180bf6-8ec9-4e03-8ad3-7e17a7b54fe4']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@65.2.63.196:/opt/apache-tomcat-9.0.54/webapps"
}
}

stage('SendEmailNotification'){

emailext body: '''Build Over..

Regards,
Mannem Bhargav.''', subject: 'Build Over', to: 'bhargavmannem136@gmail.com'
}

*/

}
