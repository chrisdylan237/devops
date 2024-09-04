pipeline {
    agent any

    stages {
        stage('Clone Git Repository') {
            steps {
                // Clone the repository with the specified branch
                git branch: 'main', url: 'https://github.com/chrisdylan237/devops.git'
            }
        }

        stage('Change Directory to DevOps') {
            steps {
                // Navigate to the 'devops' directory
                dir('devops') {
                    script {
                        // Print the current directory to confirm the change
                        sh 'pwd'
                    }
                }
            }
        }

        stage('List Directory Contents') {
            steps {
                // List the contents of the 'devops' directory
                dir('devops') {
                    sh 'ls -l'
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                // Run the Ansible playbook with the specified inventory file
                dir('devops') {
                    sh 'ansible-playbook -i inventory.yml playbook.yml'
                }
            }
        }
    }

    post {
        always {
            // Clean up workspace after the build
            cleanWs()
        }
    }
}

