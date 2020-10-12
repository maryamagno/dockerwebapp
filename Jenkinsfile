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
        bat 'mkdir Module2-test'
        dir("Module2-test"){
            git branch: "main",
            credentialsId: 'marya-github',
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
    
    stage('Push Version Back to Git') {     
        dir("Module2-test"){
           withCredentials([usernamePassword(credentialsId: 'marya-github', passwordVariable: 'pass', usernameVariable: 'user')]) {
                bat 'echo %user%'
                bat 'git config --global user.email "maryamagno@gmail.com"'
                bat 'git config --global user.name "Marya"'
                bat 'git add version.yml"
                bat 'git commit -m "Version updated via Jenkins Pipeline"'
                bat('git push https://github.com/maryamagno/module2.git HEAD:main')       
            }
        }
    }    
}
