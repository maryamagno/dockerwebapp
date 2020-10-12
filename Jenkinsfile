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
      
        dir("Module2"){
            script {
               def currentVersion = readFile(file: 'version.yml')
               println(currentVersion)
                
               def versionToDeploy = "1.0.2-abcdefg"
               writeFile(file: 'version.yml', text: versionToDeploy)
                
               def versionInYml = readFile(file: 'version.yml')
               println(versionInYml)                               
            }
            
            git add version.yml
            git commit -m 'changed version via jenkins pipeline'
           
        }
    }
}
