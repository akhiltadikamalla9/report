pipeline{
    agent any 
    stages {
        stage('Clone') {
        steps {
            echo "ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ"
            git url: 'https://github.com/akhiltadikamalla9/devops.git'
          }
    }
    stage('Reading file of another repository') {
            steps {
                script {
                    sh ' pwd '
                    echo "BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB"
                    def fileContents = readFile('report.txt')
                    echo "File contents: ${fileContents}"
                }
            }
        }
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
            curl -F file=@report.txt -F"initial_comment=Automation results" -F channels=#jenkinsslack -H "Authorization: Bearer $jenkinsnormal" https://slack.com/api/files.upload
            '''
          }
        }
      }
    }
    }
}
