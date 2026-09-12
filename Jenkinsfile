@Library("shared") _
pipeline {
    
    agent {label "vinod"}
    
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("code"){
            steps{
                script{
                    clone("https://github.com/rahulmauryaDevOps/django-notes-app.git", "main")
                }
            }
        }
        
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "rahulmauryadevops")
                }
            }
        }
        
        stage("push to dockerhub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "rahulmauryadevops")
                }
            }
        }
        
        stage("deploy"){
            steps{
               echo "this is Deploying your code"
               sh "docker compose up -d"
            }
        }
    }
}
