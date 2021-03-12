pipeline {
    agent any
    stages {
        stage('deploy') {
            steps {
//			sh "ansible-playbook -i inventory.txt main.yml"
				ansiblePlaybook( 
					playbook: 'main.yml',
					inventory: 'inventory.txt', 
//				credentialsId: 'sample-ssh-key', 
					)
				}
            }
		}
  
}
