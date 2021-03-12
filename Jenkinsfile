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
				script {
					new File('./inventory.txt').eachLine { line ->
						println line
					}
				}
//				 sh '''#!/bin/bash
//				 while read HOST; do echo $(curl $HOST:8080); done < inventory.txt
//				 '''
			}
		}
	}
}
