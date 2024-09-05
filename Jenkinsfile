pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/dariolad/JenkinsRepoTest.git', branch: 'main'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
        }
    }
}
