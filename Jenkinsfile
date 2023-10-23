pipeline{
    agent any {
    stages {
        stage('Read File') {
            steps {
                script {
                    def fileContents = readFile('report.txt')
                    echo "File contents: ${fileContents}"
                }
            }
        }
    }
    }
}
