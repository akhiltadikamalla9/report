pipeline{
    agent any 
    stages {
        stage('Read File') {
            steps {
                script {
                    echo "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                    def fileContents = readFile('report.txt')
                    echo "File contents: ${fileContents}"
                }
            }
        }
        stage('posting the report on slack channel') {
      steps {
        script {
          withCredentials([string(credentialsId: 'jenkinsnormal', variable: 'jenkinsnormal')]) {
           sh '''
            pwd
            ls -l
            curl -F file=@report.txt -F"initial_comment=Automation results" -F channels=#jenkinsslack -H "Authorization: Bearer $jenkinsnormal" https://slack.com/api/files.upload
            '''
          }
        }
      }
    }
    }
}
