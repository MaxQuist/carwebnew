node('ubuntu-Appserver-3120')
{

def app
stage('Cloning Git')
{
    /* Make sure we have the repository cloned to the workspace */
    checkout scm
}

stage('Build-and-tag')
{
    /* This builds the image, this is synonomous to docker build using the command */
    app = docker.build('xamq/car_docker_repo')
}

stage('Push to docker')
{
    docker.withRegistry('https://registry.hub.docker.com', 'maxq')
}

stage('Deploy')
{
    sh "docker-compose down"
    sh "docker-compose up -d"
}

}