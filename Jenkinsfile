pipeline {
    agent any

    stages {
        stage('Build') {
            
            
            
            steps {
                
                echo 'Building..'
                echo "=============================> image_tag: ${env.image_tag}"
                echo "=============================> branch: ${env.branch}"
                echo "=============================> 1 commit"
                echo "=============================> GIT_PREVIOUS_COMMIT: ${env.GIT_PREVIOUS_COMMIT}"
                echo "=============================> GIT_COMMIT: ${env.GIT_COMMIT}"
                echo "=============================> GIT_BRANCH: ${env.GIT_BRANCH}"
                echo "=============================> TAG_NAME: ${env.TAG_NAME}"
                
                

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
