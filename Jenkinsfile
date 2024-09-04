pipeline {
    agent any

    stages {
        stage('Clone Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/chrisdylan237/devops.git'
            }
        }

        stage('List Workspace Contents') {
            steps {
                script {
                    // List contents of the workspace to check directory structure
                    sh '''
                    ls -l
                    '''
                }
            }
        }

        stage('Change Directory to DevOps') {
            steps {
                script {
                    // Check if 'devops' directory exists and change directory
                    sh '''
                    if [ -d "devops" ]; then
                        cd devops
                        echo "Changed directory to devops"
                    else
                        echo "Directory 'devops' does not exist"
                        exit 1
                    fi
                    pwd
                    '''
                }
            }
        }

        stage('List Directory Contents') {
            steps {
                script {
                    // List contents of the 'devops' directory
                    sh '''
                    ls -l
                    '''
                }
            }
        }

        stage('Verify Playbook and Inventory Files') {
            steps {
                script {
                    // Verify presence of playbook and inventory files
                    sh '''
                    ls -l playbook.yml inventory.yml
                    '''
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    // Run Ansible playbook
                    sh '''
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
