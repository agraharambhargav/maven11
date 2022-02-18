
   
pipeline
{
    agent any
    stages
    {
        stage('ContinousDownlaod_loans')
        {
            steps
            {
                git 'https://github.com/agraharambhargav/maven.git'
            }
        }
          stage('ContinousBuild_loans')
        {
            steps
            {
                sh 'mvn package'
            }
        }
     }
}
