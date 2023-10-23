pipeline{
    agent any {
    stages {
        stage('Read File') {
            steps {
                script {
                    def fileContents = readFile('README.md')
                    echo "File contents: ${fileContents}"
                }
            }
        }
    }
    }
}
