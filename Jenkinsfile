pipeline {
    agent {
        label "ansible_docker"
    }

    stages {
        stage('prepare_node') {
            steps {
                git 'https://github.com/Exraydi/jenkins.git'
                sh 'ansible-vault decrypt secret --vault-password-file vault_pass'
                sh 'ansible-galaxy install -r requirements.yml -p roles'
                sh 'ansible-playbook site.yml -i inventory/prod.yml'
            }
        }
    }
}
