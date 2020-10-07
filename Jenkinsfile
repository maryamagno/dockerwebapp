node {
    checkout scm
    
    def registry_url = "https://registry.hub.docker.com/"
    docker.withRegistry(${registry_url}, 'marya-dockerhub-id') {
        echo("Building...")
        def customImage = docker.build("marya/testdockerapp")                
    }
    
    docker.withRegistry(${registry_url}, 'marya-dockerhub-id') {
        echo("Pushing...")      
        bat "docker login -u maryamagno -p N3tw0rk@123 ${registry_url}"

        customImage.push()
    }
}
