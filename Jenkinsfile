  pipeline {
    agent any

    environment {
        PLAYBOOK_FILE = "/home/ubuntu/playbook2.yaml"
        INVENTORY_FILE = "/home/ubuntu/inventory2"
    }

    stages {
        stage('Download Playbook') {
            steps {
                echo "Downloading playbook2.yaml file directly to ${PLAYBOOK_FILE}..."
                sh """
                    curl -sSL -H "Cache-Control: no-cache" -o ${PLAYBOOK_FILE} https://github.com/Ashwani3636/capstone/blob/369fd59dcd1b91e822b8bdf2ac3765bf0233d0f9/playbook2.yaml
                    curl -s https://api.github.com/repos/Ashwani3636/capstone/commits/main | grep sha
                """
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                echo "Executing Ansible playbook..."
                sh """
                    sudo ansible-playbook -i ${INVENTORY_FILE} ${PLAYBOOK_FILE}
                """
            }
        }

    }

    post {
        failure {
            echo 'Deployment failed. Please check the logs.'
        }
        success {
            echo 'Deployment completed successfully!'
        }
    }
}
