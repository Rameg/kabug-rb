pipeline{
    agent {
        docker{
            image 'ruby'
        }
    }
    
    stages {
        stage('Build') {
            steps{
                echo 'Building or Resolve Dependecies'
                sh 'gem install bundler'
            }
        }
        stage('Test') {
            steps{
                echo 'Running Regression testes'
            }
        }
        stage('UAT') {
            steps{
                echo 'Wait for User Acceptance'
                input(message: 'Go to production?', ok: 'Yes')
            }
        }
        stage('Prod') {
            steps{
                echo 'WebApp is Ready :)'
            }
        }
    }
}