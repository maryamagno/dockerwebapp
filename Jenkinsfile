node {
    checkout scm
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Building...")
        def customImage = docker.build("marya/testdockerapp")     
        sh "docker images"
    }
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Pushing...")      

        docker.image('https://registry.hub.docker.com/repository/docker/marya/testdockerapp').push()
    }
}
