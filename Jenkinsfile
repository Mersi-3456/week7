pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo "Build Docker image"
                bat"docker builder -t mypythonflaskapp ."
            }
        }
        stage('Run'){
            steps{
                echo "Run application in Docker Container"
                bat "docker rm -f mycontainer || exit 0"
                bat "docker run -d -p 5000:5000 --name myconatiner mypythonflaskapp"
            }
        }
    }
    post{
        success{
            echo 'Pipeline completed successfully!'
        }
        failure{
            echo 'Pipeline failer. Please check the logs.'
        }
    }
}