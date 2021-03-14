pipeline {
    agent any
    stages {
        stage('deploy') {
            steps {
				ansiblePlaybook( 
					playbook: 'main.yml',
					inventory: 'inventory.txt' 
					)
				}
            }
		stage('test') {
			steps {
				script {
					def file = readFile('inventory.txt')
					def lines = file.readLines()
					for (item in lines) {
						sh 'curl "${item}":8080'
					}
				}
			}
		}
	}
}
