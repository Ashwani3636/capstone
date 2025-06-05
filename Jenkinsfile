pipeline {
  agent any

  environment {
    ANSIBLE_HOST_KEY_CHECKING = 'False'
  }

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/Ashwani3636/capstone.git'
      }
    }

    stage('Deploy to AWS and Azure') {
      steps {
        sh 'ansible-playbook -i /home/ubuntu/inventory2.ini /home/ubuntu/playbook2.yaml'
      }
    }
  }

  post {
    success {
      echo 'Deployment Successful!'
    }
    failure {
      echo 'Deployment Failed.'
    }
  }
}
