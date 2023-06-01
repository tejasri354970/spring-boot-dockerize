node {
agent any

tools{
maven 'maven3.9.2'

}

stage('CheckOutCode'){
git 'https://github.com/tejasri354970/spring-boot-dockerize.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
 }
 
 stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t target/spring-boot-docker.jar .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                   sh 'docker login -u tejasudheer -p ${teja@354970}'

}
                   sh 'docker push target/spring-boot-docker.jar .'
                }
            }
        }
}
