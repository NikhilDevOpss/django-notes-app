@Library("shared") _
pipeline{
    agent {label "ec2"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello() 
                }
            }
        }
        stage("Code"){
            steps{
                script{
                   clone("https://github.com/NikhilDevOpss/django-notes-app.git","main")
                }
               
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","nikhil074")
                }
            }
        }
        stage("Push To Docke Hub"){
            steps{
                script{
                    docker_push("notes-app","latest","nikhil074")
                }
                    
                }
        }
        stage("Deploy"){
            steps{
                echo "Deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
