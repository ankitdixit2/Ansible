node {
    checkout scm
    stage('build') {
        /* Create docker swarm */
            sh "ansible-playbook -i inventory/hosts playbooks/swarmcluster.yml"          
            
    }
}
