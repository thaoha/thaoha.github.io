node {
  def app
  
  stage('Clone repository') {
      checkout scm
  }

  stage('Build image') {
    app = docker.build("thaoha/homepage")
  }

  stage('Test image') {
    app.inside {
      sh 'echo "Tests passed"'
    }
  }

  stage('Push image') {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credential') {
      app.push('latest')
    }
  }
}
