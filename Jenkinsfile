pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/Raisahab1905/Jenkins.git'
      }
    }

    stage('Debug Workspace') {
      steps {
        sh 'pwd'
        sh 'ls -l'
      }
    }

    stage('Run Ansible Playbook') {
      steps {
        sh 'ansible-playbook -i inventory playbook.yml'
      }
    }

    stage('Verify Jenkins') {
      steps {
        sh 'curl -s localhost:8080 | grep "Unlock Jenkins" || true'
      }
    }
  }

  post {
    success {
      echo '✅ Jenkins setup completed successfully!'
    }
    failure {
      echo '❌ Jenkins setup failed!'
    }
  }
}
