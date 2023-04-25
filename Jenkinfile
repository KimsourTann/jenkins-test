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
    }
}
