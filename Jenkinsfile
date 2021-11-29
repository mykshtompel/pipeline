pipeline {
    agent any

    environment {
        git_com = sh(returnStdout: true, script: 'git rev-parse --short=12 HEAD').trim()
        git_previous_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=1 --max-count=1`").trim()
        git_tag = sh(returnStdout: true, script: "git describe --abbrev=0 --tags `git rev-list --tags --skip=0 --max-count=1`").trim()
        git_log = sh(returnStdout: true, script: "git log --pretty=oneline ^${git_previous_tag} ${git_tag}").trim()
        git_number_of_commits = sh(returnStdout: true, script: "git rev-list --count ^${git_previous_tag} ${git_tag}").trim()
        
    }
    
    
    stages {
        stage('Build') {
            
            
            
            steps {
                script {
                    currentBuild.displayName = "#${env.BUILD_NUMBER}  rn-portal:${env.git_com}--${env.image_tag}--#${git_number_of_commits}"
                    change_log = getChangeString()
                    checkout([$class: 'GitSCM',
                               branches: [[name: '*/refs/tags/5.0']],
                               userRemoteConfigs: [[credentialsId: '44c2f71b-79a4-45c8-9b68-42e1e4d5770f', url: 'https://github.com/mykshtompel/pipeline.git']]
                               changelog: false,
                               poll: false
                    ])
                    
                }
                
                
                lastChanges format:'SIDE',matching: 'LINE',specificRevision: '4.2'
                echo 'Building..'
                echo "=============================> git_com: ${env.git_com}"
                echo "=============================> git_previous_tag: ${env.git_previous_tag}"
                echo "=============================> git_tag: ${env.git_tag}"
                echo "=============================> git_log: ${env.git_log}"
                echo "=============================> git_number_of_commits: ${env.git_number_of_commits}"
                
                
                echo "=============================> image_tag: ${env.image_tag}"
                echo "=============================> branch: ${env.branch}"
                echo "=============================> 54 commit"
                
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

@NonCPS
def getChangeString() {
 MAX_MSG_LEN = 100
 def changeString = ""

 echo "Gathering SCM changes"
 def changeLogSets = currentBuild.changeSets
 for (int i = 0; i < changeLogSets.size(); i++) {
 def entries = changeLogSets[i].items
 for (int j = 0; j < entries.length; j++) {
 def entry = entries[j]
 truncated_msg = entry.msg.take(MAX_MSG_LEN)
 changeString += "- ${truncated_msg} [${entry.author}]\n"
 }
 }

 if (!changeString) {
 changeString = " - No new changes!!!"
 }
 return changeString
}
