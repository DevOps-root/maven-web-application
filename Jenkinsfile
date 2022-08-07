pipeline
{

agent any

tools{
maven 'maven3.6.2'

}
stages{

stage('CloneScm')

{
step{
git branch: 'master', credentialsId: '72d42551-495e-414f-87ac-87693b5d04ec', url: 'https://github.com/DevOps-root/maven-web-application.git'
}
}

 stage('Build')
{
  steps{
  sh  "mvn clean package"
  }
}
	
}
}
