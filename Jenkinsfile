pipeline {
    agent any
    environment {
        registry = "mohamedmahrous/simple-devops-image"
        registryCredential = "docker-cred"
        REPORTING_EMAIL = "mmahrous924@gmail.com"
    }
    stages{

        stage('building image ') {
            steps {
                sh 'docker build -t mohamedmahrous/simple-devops-image:go-web . '
                sh 'echo1'
            }
        }   
       
        stage('pushing image') {
            steps {
                script {
                    docker.withRegistry("", registryCredential) {
                        sh 'docker push mohamedmahrous/simple-devops-image:go-web '
                    }
            }
            
        }
       
    }


  }
          post {
                failure {
                    mail bcc: "", body: "Project: $JOB_NAME<br>Build Number: $BUILD_NUMBER<br>build URL: $BUILD_URL", cc: "", charset: "UTF-8", from: "", mimeType: "text/html", replyTo: "", subject: "ERROR CI: Project name -> $JOB_NAME", to: "$REPORTING_EMAIL";  
                }
            } 
}
