pipeline {
    agent any
    
    // triggers {
    //     githubPush()
    

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git branch: 'main', url: 'https://github.com/tranhoanghatb/ansible_jenkins.git'
            }
        }
        
        stage('Update Production Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'administrator', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'create_prod_site.yml'
                
            }
        }
        stage('Clone to Dev Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'root', credentialsId: 'administrator', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'clone_prod_site.yml'
                
            }
        }
    }
}

