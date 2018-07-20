def notifySlack(String buildStatus = 'STARTED') {
    // Build status of null means success.
    buildStatus = buildStatus ?: 'SUCCESS'
    
    def msg = "${buildStatus}: `${env.JOB_NAME}` #${env.BUILD_NUMBER}:-Docker Swarm is deployed on AWS VMs by shrilekha.s"

    slackSend(message: msg)
}

node {
    checkout scm
    stage('build') {
        /* Create docker swarm */
         // sh "sudo ansible-playbook -i /etc/ansible/inventory/hosts /etc/ansible/playbooks/eia-swarmcluster.yml" 
            sh "sudo ansible-playbook /etc/ansible/playbooks/eia-swarmcluster.yml"
        /* dir ('/etc/ansible') {
    sh 'pwd'
} */            
    }
    try {      
        notifySlack(currentBuild.result)
        // Existing build steps.
    } catch (e) {
        currentBuild.result = 'FAILURE'
        throw e
    } 
}
