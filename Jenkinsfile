def user
node {
  
  user: 'Tannkimsour'
  
  emailext mimeType: 'text/html',
                 subject: "[Jenkins]${currentBuild.fullDisplayName}",
                 to: "Tann.kimsour@cellcard.com.kh",
                 body: '''<a href="${BUILD_URL}input">click to approve</a>'''
}

pipeline {
    agent any
    stages {
       
        stage('deploy') {
            input {
                message "Should we continue?"
                ok "Yes"
            }
           
            steps {
                sh "echo 'describe your deployment' "
            }
        }
        stage('Push Image to Docker Hub'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'github-id', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]) {    
                        sh '''
                        git remote set-url origin https://$GIT_USERNAME:$GIT_PASSWORD@github.com/$GIT_USERNAME/jenkins-test.git
                        git checkout master
                        git merge origin/dev
                        git push -f origin master
                        '''
                    }
                }
            }
        }

         stage('final') {
           
           
            steps {
                sh "echo 'Final Step' "
            }
        }
    }
}

