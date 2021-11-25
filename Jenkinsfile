pipeline {
    agent any

    stages {
        stage('Build') {
            
            
            
            steps {
                script{
                    currentBuild.displayName = "###${env.BUILD_NUMBER}###"
                    gitChangelog from: [type: 'COMMIT', value: '${GIT_PREVIOUS_COMMIT}'], returnType: 'STRING', to: [type: 'COMMIT', value: '${GIT_COMMIT}']
                }

                echo 'Building..'
                echo "=============================> image_tag: ${env.image_tag}"
                echo "=============================> branch: ${env.branch}"
                echo "=============================> 2 commit after merge"
                echo "=============================> GIT_PREVIOUS_COMMIT: ${env.GIT_PREVIOUS_COMMIT}"
                echo "=============================> GIT_COMMIT: ${env.GIT_COMMIT}"

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
