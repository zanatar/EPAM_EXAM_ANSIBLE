node {
    stage('deploy') {
		ansiblePlaybook( 
		playbook: 'main.yml',
		inventory: 'inventory.txt' 
		)
    }
	stage('test') {
		def file = readFile('inventory.txt')
		def lines = file.readLines()
		for (item in lines) {
			def response = httpRequest '''http://"${item}":8080'''
			println("Status: "+response.status)
			println("Content: "+response.content)
		}
	}
}
