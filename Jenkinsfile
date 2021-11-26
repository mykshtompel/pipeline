pipeline {
    agent any

    environment {
        git_com = sh(returnStdout: true, script: 'git rev-parse --short=12 HEAD').trim()
        git_previous_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=1 --max-count=1`").trim()
        git_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=0 --max-count=1`").trim()
        git_log = sh(returnStdout: true, script: "git log --pretty=oneline ^${git_previous_tag} ${git_tag}").trim()
        git_number_of_commits = sh(returnStdout: true, script: "git rev-list --count ^${git_previous_tag} ${git_tag}").trim()
        git_log_head = sh(returnStdout: true, script: "git log --pretty=oneline ${git_tag}...HEAD").trim()
        git_number_of_commits_head = sh(returnStdout: true, script: "git rev-list --count ${git_tag}...HEAD").trim()
        
            
            
    }
    
    
    stages {
        stage('Build') {
            
            
            
            steps {
                script {
                            currentBuild.displayName = "#${env.BUILD_NUMBER}  rn-portal:${env.git_com}--${env.image_tag}--#${git_number_of_commits}--#${git_number_of_commits_head}"
                            
                }
                
                echo 'Building..'
                echo "=============================> git_com: ${env.git_com}"
                echo "=============================> git_previous_tag: ${env.git_previous_tag}"
                echo "=============================> git_tag: ${env.git_tag}"
                echo "=============================> git_log: ${env.git_log}"
                echo "=============================> git_number_of_commits: ${env.git_number_of_commits}"
                echo "=============================> git_log_head: ${env.git_log_head}"
                echo "=============================> git_number_of_commits_head: ${env.git_number_of_commits_head}"
                
                
                echo "=============================> image_tag: ${env.image_tag}"
                echo "=============================> branch: ${env.branch}"
                echo "=============================> 17 commit"
                
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
