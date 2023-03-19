pipeline {
    agent any
    tools{
        maven 'maven3.9.1'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Java-Techie-jt/spring-boot-dockerize']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t spring-boot-dockerize.jar .'
                }
            }
        }
       stage("Push Docker image") {
            steps {
                sh "docker login -u tejasudheer -p Teja@354970"
                sh "docker build -t tejasudheer/spring-boot-dockerize.jar ."
                sh "docker push tejasudheer/spring-boot-dockerize.jar"
            
            }      
       }           
  } 
}
                    
            

                
                 
            
            
            
             
        
