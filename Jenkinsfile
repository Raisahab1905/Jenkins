pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Raisahab1905/Jenkins.git'
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
                sh 'curl -I http://localhost:8080'
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
