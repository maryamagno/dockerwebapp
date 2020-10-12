node {
    def workspace = pwd()
    
    stage ('First'){
        checkout scm

        docker.withRegistry('https://registry.hub.docker.com/', 'marya-dockerhub-id') {

            echo("Building with tag...")
            bat "docker build -t maryamagno/myfirstimage ."

            echo("Docker Images...")
            bat "docker images"

            echo("Pushing...")              
            bat "docker login docker.io"
            bat "docker push maryamagno/myfirstimage"
            bat "docker login docker.io"
        }
    }
    stage ('Checkout CD'){
        bat 'mkdir -p Module2'
        dir("Module2")
        {
            git branch: "main",
            credentialsId: 'marya-github-id',
            url: 'https://github.com/maryamagno/module2.git'
        }
        echo workspace
        
        bat 'cd Module2'
        script {
           def data = readFile(file: 'version.yml')
           println(data)
        }
    }
}
