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
		stage('test') {
			steps {
				sh ([script: 'while read HOST; do curl $HOST:8080; done < inventory.txt'])
			}
		}
	}
}
