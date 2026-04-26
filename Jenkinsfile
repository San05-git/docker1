pipeline{
  agent any
  environment{
    DOCKER_IMAGE= 'sannidhi005/docker1:v1'
  }
  stages{
    stage('Build Docker Image'){
      steps{
        bat 'docker build -t %DOCKER_IMAGE% .'
      }
    }
    stage('Login to DockerHub'){
      steps{
        withCredentials([usernamePassword(
          credentialsId: 'newtoken1',
          usernameVariable: 'USER',
          passwordVariable: 'PASS'
          )]){
          bat 'docker login -u %USER% -p %PASS%'
        }
      }
    }
    stage('Push Docker Image'){
      steps{
        bat 'docker push %DOCKER_IMAGE%'
      }
    }
  }
}
