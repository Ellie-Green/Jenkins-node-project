pipeline{
    agent any
    stages{
        stage("cleanup"){
            steps{
                sh "docker rm -f \$(docker ps -a -q) || true"
                sh "docker network create new-network || true" 
            }
        }
        stage("build"){
            steps{
                sh"docker build -t node-image ."
            }
        }
        stage("run"){
            steps{
                sh "docker run -d --name node-project --network new-network node-image"
                }
        }
    }
}