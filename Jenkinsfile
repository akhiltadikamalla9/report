pipeline{
    agent any 
    stages {
    stage('Reading file of another repository') {
            steps {
                script {
                        sh 'pwd'
                        echo 'aaaaaaaaaaaaaaaaaaaaa'
			echo "${ENVIRONMENT}"
			echo 'bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb'
			def fileName = params.get('ENVIRONMENT') + '.txt'
			echo "${fileName}"
			if ("$fileName".exists()) {
			checkout([$class: 'GitSCM', branches: [[name: 'main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/akhiltadikamalla9/devops.git']]])
			echo "Reading file: ${fileName}"
			def fileContent = readFile "$fileName"
			echo 'ffffffffffffffffffffffffffffffffffffffff'
			echo fileContent
			sh """
       				touch report1.txt
	   			echo "112222222111111111111111111111111"
	   			cp $fileName report1.txt
       				echo "11111111111111111111111111"
			       	sed -i "/tsb-onboarding-user-persistence-validator/d" report1.txt
	 			 echo "22222222222222222222222222"
                               echo "tsb-onboarding-user-persistence-validator 06-11-2023-04-48\n" >> report1.txt
			       echo report1.txt
			    """
			def fileContent1 = readFile 'report1.txt'
			sh """
			curl -v POST -H 'Content-type: application/json' --data '{"text": "image tag details \n: ${fileContent1}"}' https://hooks.slack.com/services/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
   			"""
			echo "44444444444444444444444444444"
			}else {
			  println "File not found: ${fileName}"
			}
                }
            }
        }
    }
}
