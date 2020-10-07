node {
    checkout scm
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Building...")        
        bat "docker build ."
        
        echo("Tagging...")
        bat "docker tag testonly maryamagno/testdockerapp"
        
        echo("Docker Images...")
        bat "docker images"
        
        echo("Pushing...")              
        bat "docker login docker.io"
        bat "docker push maryamagno/testonly"
        bat "docker login docker.io"
    }
   
}
