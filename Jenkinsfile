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
				def file = readFile('inventory.txt')
				def lines = file.readLines()
				for (item in lines) {
					curl "${item}":8080
			}
		}
	}
}
