pipeline
{
    agent any
    stages
    {
        stage('ContinousDownlaod_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/agraharambhargav/maven11.git'
                    }
                    catch(Exception e1)
                    {
                      mail bcc: '', body: 'Jenkins unable to download the maven code from git hub', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'github@gmail.com'
                      exit(1)
                    }
                }
            }    
        }
          stage('ContinousBuild_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                        mail bcc: '', body: 'Jenkins unable to create artefact the maven code from git hub', cc: '', from: '', replyTo: '', subject: 'Build failed', to: 'Dev@gmail.com'
                        exit(1)
                    }
                }
            }
           
        }
          stage('ContinousDeployment_master')
        {
            steps
            {
                script
                {
                    try
                    {
                       deploy adapters: [tomcat9(credentialsId: '7d4d7dfc-57e0-4e7b-a909-8bc59e4c5be8', path: '', url: 'http://172.31.91.12:8080')], contextPath: 'test1', war: '**/*.war' 
                    }
                    catch(Exception e3)
                    {
                      mail bcc: '', body: 'Jenkins unable to deploy tomcat on QA server', cc: '', from: '', replyTo: '', subject: 'Deploy failed', to: 'middleware@gmail.com'
                      exit(1)
                    }
                }
            }
           
        }
          stage('ContinousTesting_master')
        {
            steps
            {
                script
                {
                    try
                    {
                       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                       sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar' 
                    }
                    catch(Exception e4)
                    {
                       mail bcc: '', body: 'selenium code failed', cc: '', from: '', replyTo: '', subject: 'Testing failed', to: 'middleware@gmail.com'
                       exit(1)
                    }
                }
            }
           
        }
           stage('ContinousDelivery_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        deploy adapters: [tomcat9(credentialsId: '7d4d7dfc-57e0-4e7b-a909-8bc59e4c5be8', path: '', url: 'http://172.31.80.149:8080')], contextPath: 'prod1', war: '**/*.war'
                    }
                    catch(Exception e5)
                    {
                        mail bcc: '', body: 'Jenkins unable to deploy on prod server', cc: '', from: '', replyTo: '', subject: 'delivery failed', to: 'Delievry@gmail.com'
                    }
                }
            }
          
        }
    }  
}
