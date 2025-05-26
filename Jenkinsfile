pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Raisahab1905/Jenkins.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }

    }

    post {
        failure {
            echo '❌ Jenkins setup failed!'
        }
        success {
            echo '✅ Jenkins setup completed successfully!'
        }
    }
}
