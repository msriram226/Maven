
node('master') 
{
    stage('ContiniousDownload') 
    {
    git credentialsId: 'fc77c491-036d-42e1-af93-55125da35b03', url: 'https://github.com/msriram226/Maven.git'
}
 stage('ContiniousBuild') 
    {
        sh label: '', script: 'mvn package'
}
stage('CoontiniousDeployment') 
    {
   sh label: '', script: '''scp /home/ubuntu/.jenkins/workspace/Development/webapp/target/webapp.war  ubuntu@172.31.15.78:/var/lib/tomcat8/webapps/qaenv.war
'''
}
stage('ContiniousTesting')
{
git credentialsId: 'fc77c491-036d-42e1-af93-55125da35b03', url: 'https://github.com/msriram226/TestingNew.git'
 sh label: '', script: '''echo "Testing Passed" '''
}
stage('ContiniousDelivery') 
    {
     input message: 'Waiting for Manager Approval', submitter: 'Manager'  
   sh label: '', script: '''scp /home/ubuntu/.jenkins/workspace/Development/webapp/target/webapp.war  ubuntu@172.31.7.156:/var/lib/tomcat8/webapps/prodenv.war
'''
}
}
