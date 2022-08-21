pipeline {
  agent any
  environment {
    scannerHome = tool 'SonarQubeScanner'
    username='admin'
    appName='app_shivambindal'
    sonarAppName='sonar-shivambindal'
  }
  tools {
    nodejs 'nodejs'
  }
  stages {
    stage('Build') {
      steps {
        bat 'npm i'
      }
    }
    // stage('Test case execution') {
    //   when {
    //     branch 'master'
    //   }
    //   steps {
    //     bat 'npm test'
    //   }
    // }
    // stage('Sonarqube Analysis') {
    //   when {
    //     branch 'develop'
    //   }
    //   steps {
    //     echo "Starting sonarqube analysis"
    //     withSonarQubeEnv('Test_Sonar') {
    //       bat "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${sonarAppName}"
    //     }
    //   }
    // }
    stage('Kubernetes Deployment') {
      steps {
        bat 'whoami'
        bat 'echo %Path%'
        bat 'kubectl --kubeconfig=D:/kube_prop/.kube/config apply -f k8s/deployment.yaml'
        //bat 'kubectl apply -f k8s/deployment.yaml'
      }
    }
  }
}