node {
    checkout scm
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Building...")
        def customImage = docker.build("marya/testdockerapp")                
    }
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Pushing...")      

        docker.image('https://registry.hub.docker.com/marya/testdockerapp').push()
    }
}
