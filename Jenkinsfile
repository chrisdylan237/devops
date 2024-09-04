pipeline {
    agent any

    stages {
        stage('Clone Git Repository') {
            steps {
                sh '''
                git clone https://github.com/chrisdylan237/devops.git
                '''
            }
        }

        stage('Change Directory to DevOps') {
            steps {
                script {
                    // Change directory to 'devops' and verify
                    sh '''
                    cd devops
                    pwd
                    '''
                }
            }
        }

        stage('List Directory Contents') {
            steps {
                script {
                    // Change directory to 'devops' and list contents
                    sh '''
                    cd devops
                    ls -l
                    '''
                }
            }
        }

        stage('Verify Playbook and Inventory Files') {
            steps {
                script {
                    // Change directory to 'devops' and verify specific files
                    sh '''
                    cd devops
                    ls -l playbook.yml inventory.yml
                    '''
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    // Change directory to 'devops' and run Ansible playbook
                    sh '''
                    cd devops
                    ansible-playbook -i inventory.yml playbook.yml
                    '''
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
