node {
    checkout scm
    stage('build') {
        /* Create docker swarm */
            sh "sudo -S ansible-playbook -i /etc/ansible/inventory/hosts /etc/ansible/playbooks/swarmcluster.yml"  
        /* dir ('/etc/ansible') {
    sh 'pwd'
} */
            
    }
}
