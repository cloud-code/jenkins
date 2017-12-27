pipeline {
	def builtImage
	agent {
		label 'docker'
	}
	stages {
		stage('Cloning Repo...') {
			echo 'Cloning GitHub Repository..'
			steps {
				checkout scm
			}
		}
		stage('Build Image') {
			steps {
				echo 'Building Image...'
				builtImage = docker.build("sgdpro/jenkinstest")
			}
		}
		stage('Test') {
			steps {
				echo 'Testing Image...'
				builtImage.inside {
					sh 'echo "Testing the image, stub for now..."'
				}
			}
		}
		stage('Deploy') {
			steps {
				echo 'Deploying - Publishing Image....'
				builtImage.push("${env.BUILD_ID}")
				builtImage.push("latest")
			}
		}
	}
}
/* node("docker") {
	def builtImage
	checkout scm
	builtImage = docker.build("sgdpro/jenkinstest")
	builtImage.push("${env.BUILD_ID}")
	builtImage.push("latest")
} */

