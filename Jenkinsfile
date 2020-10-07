node {
    checkout scm
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
       
        echo("Building with tag...")
        bat "docker build -t maryamagno/myFirstImage ."
        
        echo("Docker Images...")
        bat "docker images"
        
        echo("Pushing...")              
        bat "docker login docker.io"
        bat "docker push maryamagno/myFirstImage"
        bat "docker login docker.io"
    }
   
}
