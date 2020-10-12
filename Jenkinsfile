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
        bat 'mkdir Module2'
        dir("Module2"){
            git branch: "main",
            credentialsId: 'marya-github-id',
            url: 'https://github.com/maryamagno/module2.git'
            
            script {
               def currentVersion = readFile(file: 'version.yml')
               println(currentVersion)
                
               def versionToDeploy = "1.0.2-hijklmn"
               writeFile(file: 'version.yml', text: versionToDeploy)
                
               def versionInYml = readFile(file: 'version.yml')
               println(versionInYml)                               
            }            
        }         
    }
    
    stage ('Update'){
        dir("Module2"){
            bat "git add ."
            bat "git commit -m 'Updated version via Jenkins Pipeline'"
            bat "git push origin main"
        }
    }
}
