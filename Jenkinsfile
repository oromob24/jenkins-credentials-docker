pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh 'docker build -t orlaromo/jenkins-web:latest .'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
          sh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
          sh 'docker push apasoft/jenkins-web:latest'
        }
      }
    }
    stage('Docker Run') {
      steps {
        sh 'docker build -t orlaromo/jenkins-web:latest .'
      }
    }
  }
}
