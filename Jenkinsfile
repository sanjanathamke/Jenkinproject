pipeline {
    agent {label "Jenkinagent"}
    
    stages{
      stage('code'){
            steps{
                echo "code"
                }
            }

        stage('Build'){
            agent {
                docker {
                    image 'sanjanathamke/nodejs'
                    reuseNode true
                }
                    
                }
            steps{
                echo "building"
                sh 'node --version'
                }  
            }
            stage('Test'){
            steps{
                echo "Testing"
                }
            }
        
        stage('Deploy'){
            steps{
                sh "docker run -d sanjanathamke/nodejs"
            }
        }
    }
}
