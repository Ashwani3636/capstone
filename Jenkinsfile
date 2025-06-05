  pipeline {
    agent any

    environment {
        PLAYBOOK_FILE = "/home/ubuntu/playbook2.yaml"
        INVENTORY_FILE = "/home/ubuntu/inventory2"
    }

    stages {
        stage('Download Playbook') {
            steps {
                echo "Downloading index-azure.html file directly to ${PLAYBOOK_FILE}..."
                sh """
                    curl -sSL -H "Cache-Control: no-cache" -o ${PLAYBOOK_FILE} https://github.com/Ashwani3636/capstone/blob/d1ceaed1521f5c683ce07911fbb5df4225fad4fa/index-azure.html
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
