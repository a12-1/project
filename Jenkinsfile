node('master')
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/a12-1/project.git'
    }
    stage('ContinuousBuild') 
    {
         sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/jenkinsfile/webapp/target/webapp.war ubuntu@172.31.44.214:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/jenkinsfile/testing.jar'
    }
     stage('ContinuousDelivery')
    {
        input message: 'Waiting for Approval from the DM', submitter: 'Srinivas'
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/jenkinsfile/webapp/target/webapp.war ubuntu@172.31.83.216:/var/lib/tomcat8/webapps/prodenv.war'
    }
    
    
}

