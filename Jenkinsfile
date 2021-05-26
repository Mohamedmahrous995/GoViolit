pipeline {
    agent any
    environment {
        registry = "mohamedmahrous/simple-devops-image"
        registryCredential = "docker-cred"
        
    }
    stages{

        stage('building image ') {
            steps {
                sh 'docker build -t mohamedmahrous/simple-devops-image:go-web . '
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
}
