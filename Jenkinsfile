pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                    sh 'pwd'
                    echo 'aaaaaaaaaaaaaaaaaaaaa'
                    checkout([$class: 'GitSCM', branches: [[name: 'main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
			    def imagefile = "report.txt"
			    sh """
       				touch report1.txt
	   			cp report.txt report1.txt
       				echo "11111111111111111111111111"
			       	sed -i "/tsb-onboarding-user-persistence-validator/d" report1.txt
	 			 echo "22222222222222222222222222"
                               echo "tsb-onboarding-user-persistence-validator 06-11-2023-04-48\n" >> report1.txt
			       echo report1.txt
			    """
			def fileContent = readFile 'report1.txt'
			sh """
			curl -v POST -H 'Content-type: application/json' --data '{"text": "image tag details \n: ${fileContent}"}' https://hooks.slack.com/services/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
   			"""
			echo "44444444444444444444444444444"
                }
            }
        }
    }
}
