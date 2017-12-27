node("docker") {
    def builtImage
    stages {
        stage('Cloning Repo...') {
            echo 'Cloning GitHub Repository..'
            checkout scm
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
                docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-creds') {
                    builtImage.push("${env.BUILD_ID}")
                    builtImage.push("latest")
                }
            }
        }
    }
}
