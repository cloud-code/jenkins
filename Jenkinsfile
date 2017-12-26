node("docker") {
	checkout scm
	docker.withRegistry('https://hub.docker.com', '2b3cde07-40aa-439e-b434-64f48cc494d5') {
		def customImage = docker.build("jenkinstest:${env.BUILD_ID}")
		customImage.push()
	}
}
