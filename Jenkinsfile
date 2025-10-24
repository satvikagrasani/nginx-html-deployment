pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = "/etc/ansible/hosts"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/satvikagrasani/nginx-html-deployment.git'
            }
        }

        stage('Deploy to AWS and Azure') {
            steps {
                sh 'ansible-playbook -i $ANSIBLE_INVENTORY ansible/deploy_html.yml'
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
