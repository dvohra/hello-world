node("docker") {
    docker.withRegistry('https://index.docker.io/v1/', 'dvohra-dockerhub') {
     
        git url: "https://github.com/dvohra/hello-world.git", credentialsId: 'dvohra-github'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        sh "sudo service docker start"
        sh "sudo service docker status"
        def app = docker.build "dvohra/hello-world"
    
        stage "publish"
        app.push 'latest'
    }
}
