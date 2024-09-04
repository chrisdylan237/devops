pipeline {
    agent any

    stages {
        stage('Clone Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/chrisdylan237/devops.git'
            }
        }

        stage('Change Directory to DevOps') {
            steps {
                dir('devops') {
                    script {
                        sh 'pwd'
                    }
                }
            }
        }

        stage('List Directory Contents') {
            steps {
                dir('devops') {
                    sh 'ls -l'
                }
            }
        }

        stage('Verify Playbook and Inventory Files') {
            steps {
                dir('devops') {
                    sh 'ls -l playbook.yml inventory.yml'
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                dir('devops') {
                    sh 'ansible-playbook -i inventory.yml playbook.yml'
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
