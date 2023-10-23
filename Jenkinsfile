pipeline{
    agent any 
    stages {
        stage('Read File') {
            steps {
                script {
                    echo "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                    def fileContents = readFile('README.md')
                    echo "File contents: ${fileContents}"
                }
            }
        }
    }
}
