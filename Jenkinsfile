pipeline {

//   options {
//     ansiColor('xterm')
//   }

  agent {
    kubernetes {
      yamlFile 'web.yaml'
    }
  }

  stages {
    
    stage('Deploy App to Kubernetes') {     
      steps {
        container('kubectl') {
          withCredentials([file(credentialsId: 'mykubeconfig', variable: 'KUBECONFIG')]) {
            sh 'sed -i "s/<TAG>/${BUILD_NUMBER}/" myweb.yaml'
            sh 'kubectl apply -f myweb.yaml'
          }
        }
      }
    }
  
  }
}
