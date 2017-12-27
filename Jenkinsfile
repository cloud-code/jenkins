node("docker") {
	def builtImage
	checkout scm
	builtImage = docker.build("sgdpro/jenkinstest")
	builtImage.push("${env.BUILD_ID}")
	builtImage.push("latest")
}
