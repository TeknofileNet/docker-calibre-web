node("docker") {
  docker.withRegistry('hub.docker.com', 'teknofile') {
    git url: "github.com/TeknofileNet/docker-calibre-web", credentialsId: "teknofile-github"
    sh "git rev-parse HEAD > .git/commit-id"
    def commit_id = readFile('.git/commit-id').trim()
    println(commit_id)

    stage "build"
    def app = docker.build "docker-calibre-web"

    stage "publish"
    app.push 'master'
    app.push "${commit_id}"
  }
}
