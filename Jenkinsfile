pipeline{
    agent any 
    stages {
        stage('Read File') {
            steps {
                script {
                    ECHO "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
                    def fileContents = readFile('README.md')
                    echo "File contents: ${fileContents}"
                }
            }
        }
    }
}
