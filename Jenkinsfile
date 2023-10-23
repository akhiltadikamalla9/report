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
    }
}
