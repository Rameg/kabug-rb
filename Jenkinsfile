pipeline{
    agent {
        docker{
            image 'rameg/rubywd'
        }
    }
    
    stages {
        stage('Build') {
            steps{
                echo 'Building or Resolve Dependecies'
                sh 'rm -f Gemfile.lock'
                sh 'bundler install'
            }
        }
        stage('Test') {
            steps{
                echo 'Running Regression testes'
                sh 'bundle exec cucumber -p ci'
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