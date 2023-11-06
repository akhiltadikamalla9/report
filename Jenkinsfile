pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                    sh 'pwd'
                    echo 'aaaaaaaaaaaaaaaaaaaaa'
                    checkout([$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
			    def fileContent = readFile 'report.txt'
			    def imagefile = "report.txt"
		            // Print the content
		            echo fileContent
			    sh """
			       sed -i "/${msname}/d" $imagefile
                               cat $imagefile
                               echo "${msname} ${imageTag}\n" >> $imagefile
                               cat $imagefile
			       curl -v -X POST -H 'Content-type: application/json' --data '{"text": "Namespace: ${namespace} | Microservice Name: ${msname} | Image Tag: ${imageTag}"}' https://hooks.slack.com/services/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
			    """
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
