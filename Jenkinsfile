node("docker") {
	def builtImage
	stage('Cloning Repo...') {
		echo 'Cloning GitHub Repository..'
		checkout scm
	}
	stage('Build Image') {
		echo 'Building Image...'
		builtImage = docker.build("sgdpro/jenkinstest")
	}
	stage('Test') {
		echo 'Testing Image...'
		builtImage.inside {
			sh 'echo "Testing the image, stub for now..."'
		}
	}
	stage('Deploy') {
		echo 'Deploying - Publishing Image....'
		builtImage.push("${env.BUILD_ID}")
		builtImage.push("latest")
	}
}
