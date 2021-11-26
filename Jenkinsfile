pipeline {
    agent any

    environment {
        git_com = sh(returnStdout: true, script: 'git rev-parse --short=12 HEAD').trim()
        git_previous_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=1 --max-count=1`").trim()
        git_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=0 --max-count=1`").trim()
        
            
            
    }
    
    
    stages {
        stage('Build') {
            
            
            
            steps {
                script {
                            currentBuild.displayName = "#${env.BUILD_NUMBER}  rn-portal:${env.git_com}"
                            
                }
                
                echo 'Building..'
                echo "=============================> git_com: ${env.git_com}"
                echo "=============================> git_previous_tag: ${env.git_previous_tag}"
                echo "=============================> git_tag: ${env.git_tag}"
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
