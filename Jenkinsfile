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
			    def imagefile = "report.txt"
			def fileContent1 
			    sh """
			       sed -i "/tsb-onboarding-user-persistence-validator/d" $imagefile
                               echo "tsb-onboarding-user-persistence-validator 06-11-2023-04-48\n" >> $imagefile
			       echo "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
                               cp $imagefile $fileContent1
			       echo "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
			       curl -v POST -H 'Content-type: application/json' --data '{"text": "image tag details \n: ${fileContent1}"}' https://hooks.slack.com/services/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
	  			echo "ccccccccccccccccccccccccccccc"
			    """
                }
            }
        }
    }
}
