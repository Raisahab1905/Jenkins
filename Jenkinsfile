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
                sshagent(['jenkins-ssh-key']) {
                    sh 'ansible-playbook -i inventory.ini playbook.yml'
                }
            }
        }
        stage('Run Ansible Playbook') {
          steps {
           sshagent(['jenkins-ssh-key']) {
            sh '''
            pwd
            ls -l
            cat inventory.ini
            ansible-playbook -i inventory.ini playbook.yml
            '''
        }
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
