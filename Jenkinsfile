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
			    sh """
       				echo "11111111111111111111111111"
			       	sed -i "/tsb-onboarding-user-persistence-validator/d" $imagefile
	 			 echo "22222222222222222222222222"
                               echo "tsb-onboarding-user-persistence-validator 06-11-2023-04-48\n" >> $imagefile
			       echo $imagefile
			    """
			def fileContent1
			sh 'cat $imagefile >> $fileContent1'
			sh """
			curl -v POST -H 'Content-type: application/json' --data '{"text": "image tag details \n: ${fileContent1}"}' https://hooks.slack.com/services/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
   			"""
			echo "44444444444444444444444444444"
                }
            }
        }
    }
}
