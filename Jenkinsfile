node {
    checkout scm
    
    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Building...")
        def customImage = docker.build("marya/testdockerapp")     
        customImage.tag("testonly")
        
        echo("Docker Images...")
        bat "docker images"
        
        echo("Pushing...")      
        
        bat "docker login docker.io"
        bat "docker push registry.hub.docker.com/marya/testdockerapp:testonly"
    }
   
}
