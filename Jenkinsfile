@Library("Shared") _
pipeline{
    
    agent{ label "vinod"}
    
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
                    clone("https://github.com/slayerhxrsh/django-notes-app-devops.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app-devops","latest","harshsrivastava1427")
                }
                
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app-devops","latest","harshsrivastava1427")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the app"
                sh "docker compose down && docker compose up -d"
                echo "app deployed"
            }
        }
    }
}
