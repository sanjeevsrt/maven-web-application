node
{
 def mavenHome = tool name : "maven3.8.1"
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')),
 pipelineTriggers([githubPush()])])
 stage('checkout code')
 {
    git branch: 'development', credentialsId: '0ae2c486-509b-4338-9a99-f91fba8c8488', url: 'https://github.com/sanjeevsrt/maven-web-application.git'
 }
 stage('build')
 {
    sh "${mavenHome}/bin/mvn clean package" 
 }
 /*
 stage('sonarQube Report')
 {
     sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 stage("upload artifact into nexus")
 {
    sh "${mavenHome}/bin/mvn deploy" 
 }
 stage('deploy into tomcat server')
 {
     sshagent(['af279c05-d3d9-43ba-b174-c9c139691062']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@18.222.174.238:/opt/apache-tomcat-9.0.46/webapps/"
  }
  */
  stage('send email notification')
  {
      emailext body: '''Build Over.

    Regards,
    Sanjeev.''', subject: 'Build Over....', to: 'sanjus929@gmail.com'
  }
}
