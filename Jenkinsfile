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
        stage('Deploy to Staging'){
            steps {
            	timeout(time:3, unit:'DAYS'){
                    input message:'R u sure u want to do dis??'
                }
                build job: 'deploy-to-staging'
            }
        }
        stage('Deploy to Production'){
            steps {
            	timeout(time:3, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'deploy-to-prod'
            }
            post{
                success{
                    echo 'Dude, your job rocks!'
                }
				failure{
                    echo 'Dude, your job sucks!'
                }
            }
        }
    }
}
