// pipeline {
//     agent any

//     triggers {
//         githubPush()
//     }

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 git url: 'https://github.com/dariolad/JenkinsRepoTest.git', branch: 'main'
//             }
//         }
//     }

//     post {
//         always {
//             archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
//         }
//     }
// }

pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Check branch') {
            steps {
                script {
                    // Verifica se il branch non è 'main'
                    if (env.BRANCH_NAME != 'main') {
                        echo "Branch ${env.BRANCH_NAME} non è 'main', la build viene interrotta."
                        currentBuild.result = 'SUCCESS'
                        return
                    }
                }
            }
        }

        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/dariolad/JenkinsRepoTest.git', branch: 'main'
            }
        }

        // Altri stage come Build, Test, Deploy possono essere aggiunti qui
    }

    post {
        always {
            archiveArtifacts artifacts: '**/*', allowEmptyArchive: true
        }
    }
}
