node("docker") {
    checkout scm
    def customImage = docker.build("jenkinstest:${env.BUILD_ID}")
    customImage.push()
}
