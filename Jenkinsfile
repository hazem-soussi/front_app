pipeline {
agent any
    
    
    stages {
        

        stage ("1st stage : Git checkout "){
            steps{
        git branch: 'main', 
            url: 'https://github.com/hazem-soussi/front_app'
            }
        
        }
    
      

        
        stage ("Docker image build") {
            steps {
                script {
                sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                sh 'docker image tag $JOB_NAME:v1.$BUILD_ID hazem1998/$JOB_NAME:v1.$BUILD_ID '
                sh 'docker image tag $JOB_NAME:v1.$BUILD_ID hazem1998/$JOB_NAME:latest '

                }   
             }
          }
        
      
        
    
        
               
        stage ("Push image to dockerHUb") {
        
            steps {
                script {
                    withCredentials([string(credentialsId: 'docker_password', variable: 'docker_imagePWD')]) {
                        sh "docker login -u hazem1998 -p ${docker_imagePWD}"
                    sh 'docker image push hazem1998/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image push hazem1998/$JOB_NAME:latest '}
                    
                  
                    
                    
                    
          
                }
            
            }
        
        
        }
        
    
    
    }
    
    
  
}
