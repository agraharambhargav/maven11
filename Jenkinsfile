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
}
}
