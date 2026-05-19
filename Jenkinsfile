@Library("Shared") _
pipeline {
    
    agent {
        label 'vinod'
    }

    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code") {
            steps {
               script{
            clone("https://github.com/its-Aakash07/django-notes-app.git", "main")
               }
            }
        }

        stage("Build") {
            steps {
               script{
                   docker_build("notes-app","latest","itsaakash07")
               }
            }
        }

        stage("Test") {
            steps {
                echo "This is testing the code."
            }
        }

        stage("Pushing to DockerHub") {
            steps {
                script{
                    docker_push("notes-app", "latest" , "itsaakash07")
                }
            }
        }

        stage("Deploy") {
            steps {
                script{
                    dcoker_compose()
                }
            }
        }
    }
}
