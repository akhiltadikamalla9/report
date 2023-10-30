pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                    sh ' pwd '
                    checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
                    def file = /src/main/resources/report.txt
                    def fileContents = readFile('report.txt')
                    echo "File contents: ${fileContents}"
                    cat report.txt
                }
            }
        }
        stage('posting the report on slack channel') {
      steps {
        script {
            sh 'pwd'
          withCredentials([string(credentialsId: 'jenkinsnormal', variable: 'jenkinsnormal')]) {
           sh '''
            curl -F file=@report.txt -F"initial_comment=Automation results" -F channels=#jenkinsslack -H "Authorization: Bearer $jenkinsnormal" https://slack.com/api/files.upload
            '''
          }
        }
      }
    }
    }
}
