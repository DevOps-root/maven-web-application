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
sshagent(['72c8f85c-bf42-4152-a869-0c6f8a5a1c70']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@52.66.241.230:/opt/tomcat9/webapps/"
}
}

  
}
