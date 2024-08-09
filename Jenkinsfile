pipeline {
    agent any
    stages {       
        stage('Update Production Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'administrator_ssh', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'create_prod_site.yml'
                
            }
        }
        stage('Clone Production Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'administrator_ssh', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'clone_prod_site.yml'
                
            }
        }
        stage('Deploy to Dev Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'administrator_ssh', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'deploy_dev_site.yml'
                
            }
        }
    }
}

