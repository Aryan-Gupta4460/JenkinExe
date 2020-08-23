pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/Aryan-Gupta4460/JenkinExe.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          sh "docker build - < Dockerfile"
        }
      }
    }

    stage('Push Image') {
      steps{
        script {
         withCredentials([string(credentialsId: 'ARYUmedhu1@', variable: 'docker-hub')]) {
			    sh "docker login -u aryangupta4460 -p ${ARYUmedhu1@}"  {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy App to local k8s') {
      steps {
        script {
          sh 'kubectl apply -f myweb.yaml'
        }
      }
    }

  }

}
