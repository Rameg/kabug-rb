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
                sh 'bundle install'
            }
        }
        stage('Test') {
            steps{
                echo 'Running Regression testes'
                sh 'bundle exec cucumber -p ci'
                cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'logs', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
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