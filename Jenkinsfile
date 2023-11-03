pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                    sh 'pwd'
                    echo 'aaaaaaaaaaaaaaaaaaaaa'
                    checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
                    echo 'cccccccccccccccccccccccc'
                    sh 'pwd'
                    echo 'dddddddddddddddddddddddddd'
                    def file = readFile 'report.txt'
                    echo 'bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb'
                    def fileContents = "/src/main/resources/report.txt"
                    echo "File contents: ${fileContents}"
                     echo "File contents111: ${file}"
                    echo 'zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz'
                    sh 'cat report.txt'
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
