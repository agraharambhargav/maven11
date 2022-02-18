pipeline
{
    agent any
    stages
    {
        stage('ContinousDownlaod_master')
        {
            steps
            {
                git 'https://github.com/agraharambhargav/maven11.git'
            }
        }
          stage('ContinousBuild_master')
        {
            steps
            {
                sh 'mvn package'
            }
        }
          stage('ContinousDeployment_master')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.91.12:/var/lib/tomcat9/webapps/test1.war'
            }
        }
          stage('ContinousTesting_master')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
           stage('ContinousDelivery_master')
        {
            steps
            {
                input message: 'Need approvals from DM!', submitter: 'charitha'
                sh 'scp /home/ubuntu/.jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.80.149:/var/lib/tomcat9/webapps/prod1.war'
            }
        }
    }  
}
