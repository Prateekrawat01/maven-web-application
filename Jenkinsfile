node {
def mavenHome = tool name: "maven-1"

//this stage is for git clone
stage('checkout git')
{
git 'https://github.com/Prateekrawat01/maven-web-application.git'
}
//this stage is for build
stage ('build')
{
sh "$mavenHome/bin/mvn clean package"
}
//upload war to artifact
stage ('artifact')
{
sh "$mavenHome/bin/mvn deploy"
}
//deploy to tomcat
stage ('deploy tomcat')
{
sshagent(['sshtomcat1'])
{
sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.234.202.166:/opt/apache-tomcat-9.0.96/webapps"
}
}
}
