pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                    sh 'pwd'
                    echo 'aaaaaaaaaaaaaaaaaaaaa'
                    checkout([$class: 'GitSCM', branches: [[name: 'main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
			    def fileContent = readFile 'report.txt'
			    def fileContent1
			    def imagefile = "report.txt"
			    sh """
			       sed -i "/tsb-onboarding-user-persistence-validator/d" $imagefile
                               echo "tsb-onboarding-user-persistence-validator 06-11-2023-04-48\n" >> $imagefile
                               cat $imagefile
			       curl -v -X POST -H 'Content-type: application/json' --data '{"text": "image tag details \n: ${imagefile}"}' https://hooks.slack.com/services/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
			    """
                }
            }
        }
    }
}
