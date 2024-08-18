pipeline
{
    agent any
    stages
    {
        stage("Checkout the code")
        {
            steps
            {
                git url:'https://github.com/devopsak1/jenkinsrepo.git',branch:'main'
            }
        }
        stage("cleanUp stage for removing running container")
        {
            steps
            {
                sh 'docker rm -f $(ps -aq)'
                sh 'docker rmi myimage'
            }
        }
        stage("Build docker file ")
        {
            steps
            {
                sh 'docker build -t myimage .'
            }
        }
        stage("Create container ")
        {
            steps
            {
                sh 'docker run -d -p 8501:8501 myimage'
            }
        }
    }
}