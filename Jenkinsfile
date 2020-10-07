node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {
        echo("Building...")
        def customImage = docker.build("marya/testdockerapp")
        echo("Uploading...")
        /* Push the container to the custom Registry */
        customImage.push()
    }
}
