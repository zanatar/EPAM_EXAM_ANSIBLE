node {
    stage('deploy') {
		checkout scm
		ansiblePlaybook( 
		playbook: 'main.yml',
		inventory: 'inventory.txt' 
		)
    }
	stage('test') {
		def file = readFile('inventory.txt')
		def lines = file.readLines()
		for (item in lines) {
			echo "${item}"
			def uri = http://"${item}":8080
			def response = httpRequest "${uri}"
			println("Status: "+response.status)
			println("Content: "+response.content)
		}
	}
}