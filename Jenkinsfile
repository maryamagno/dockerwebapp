node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {

        def customImage = docker.build("marya/testdockerapp")
        docker logout
        docker login
        /* Push the container to the custom Registry */
        customImage.push()
    }
}
