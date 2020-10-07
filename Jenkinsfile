
def buildDockerImages() {
    echo 'Building Docker Images...'
    
    docker.build("marya/testdockerapp")
}

def publishDockerImages() {
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Pushing...")      

        docker.image('https://registry.hub.docker.com/marya/testdockerapp').push()
    }
}

pipeline {

  agent any
  stage ('Checkout') {
        steps {
            sh 'echo "Checking Out Source Code..."'
            checkout scm
        }
  }
   
    stage('Build Docker Images') {

        steps {
            buildDockerImages()
        }
    }
    
    stage('Publish Docker Images') {

        steps {
            publishDockerImages()
        }
    }
}
