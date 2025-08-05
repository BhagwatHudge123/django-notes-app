@Library("shared") _
pipeline{
    
    agent {label "bond" }
    
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
               clone("https://github.com/BhagwatHudge123/django-notes-app.git", "main")
               }
           }   
        }
        stage("Build"){
           steps{
               //echo "This is Building the code"
              // sh "whoami"
               script{
               docker_build("notes-app", "latest", "bhagwathudge")
               }
           }    
        }
        stage("Test"){
            steps{
                echo "This is testing the code"
            }  
        }
      // stage("Push to DockerHub"){
      //     steps{
              //  echo "This is pushing image to docker hub"
              //  withCredentials([usernamePassword(
              //      'credentialsId':"dockerHubCred",
              //      usernameVariable:"dockerHubUser")]){
              //  sh "docker login -u ${env.dockerHubUser} -p ${env.dockerhubPass}"
               // sh "docker image tag notes-app:latest ${env.dockerHubUser}/notes-app:latest"
               // sh "docker push ${env.dockerHubUser}/notes-app:latest"
         //      }
         //      script{
             //    docker_push("notes-app","latest","bhagwathudge")
           //      }
       //   }  
      // }
         
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                //sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker compose up -d"
            }  
        }
        
    }
}
