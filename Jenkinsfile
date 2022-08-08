node
{

def mavenHome = tool name: "maven3.6.2"

stage('ScmClone')
{
  git branch: 'master', credentialsId: '53b17209-0264-4972-a68b-8f678bc652a5', url: 'https://github.com/DevOps-root/maven-web-application.git'
}

stage('BuildArtifact')
{
sh "${mavenHome}/bin/mvn clean package"
}

stage('SonarScannerReport')
{
sh "${mavenHome}/bin/mvn sonar:sonar"
}  
  
  stage('DeployAppintoTomcatServer'){
sshagent(['65b807a6-c5c1-475c-a541-a23bb8fd1ae4']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.85.14:/opt/tomcat9/webapps/"
}
}

  
}
