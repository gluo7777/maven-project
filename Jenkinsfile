pipeline { // declarative
    agent any // how to build
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package' // shell action
            }
            post { // post-build
                success { // condition
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
