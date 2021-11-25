pipeline {
    agent any

    stages {
        stage('Build') {
            
            
            
            steps {
                script {
                            gitChangelog from: [type: 'COMMIT', value: '${env.GIT_PREVIOUS_COMMIT}'], returnType: 'STRING', to: [type: 'COMMIT', value: '${env.GIT_COMMIT}']
                            
                }
                echo 'Building..'
                echo "=============================> image_tag: ${env.image_tag}"
                echo "=============================> branch: ${env.branch}"
                echo "=============================> 2 commit after merge"

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
