pipeline
{
    agent any
    stages
    {
        stage('ContinousDownlaod')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
          stage('ContinousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
          stage('ContinousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '7d4d7dfc-57e0-4e7b-a909-8bc59e4c5be8', path: '', url: 'http://172.31.91.12:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
          stage('ContinousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline/testing.jar'
            }
        }
           stage('ContinousDelivery')
        {
            steps
            {
                input message: 'Need approvals from DM!', submitter: 'charitha'
                deploy adapters: [tomcat9(credentialsId: '7d4d7dfc-57e0-4e7b-a909-8bc59e4c5be8', path: '', url: 'http://172.31.80.149:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }  
}
