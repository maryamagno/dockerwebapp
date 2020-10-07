node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'marya-dockerhub-id') {

        def customImage = docker.build("marya/testdockerapp")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
