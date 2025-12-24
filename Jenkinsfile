@Library("Shared") _

pipeline {
    agent { label "vinod" }
    
    stages {
        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script {
                    clone("https://github.com/vatul16/django-notes-app.git", "main")
                }
            }
        }
        
        stage("Build"){
            steps{
                script {
                    docker_build("notes-app", "latest", "atulv16")
                }
            }
        }
        
        stage("Push to Docker Hub ") {
            steps{
                script {
                    docker_push("notes-app", "latest", "atulv16")
                }
            }
        }
        
        stage("Deploy"){
            steps{
                script {
                    docker_compose()
                }
            }
        }
    }
}
