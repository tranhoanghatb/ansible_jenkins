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
        
        stage('Create Production Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'administrator', credentialsId: 'administrator', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'create_prod_site.yml'
                
            }
        }
        stage('Copy to Dev Site') {
            steps {
                // Run Ansible Playbook
                ansiblePlaybook become: true, becomeUser: 'administrator', credentialsId: 'administrator', disableHostKeyChecking: true, installation: 'ansible', inventory: 'inventory', playbook: 'pull_modify_push.yml'
                
            }
        }
    }
}

