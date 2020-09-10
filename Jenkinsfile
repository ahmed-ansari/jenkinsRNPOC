pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
        PATH = "/usr/local/bin:$PATH"
    }
    tools {nodejs "NodeJS"}
    stages {
        stage('Test') {
            steps {
                sh 'echo Testing'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo Deploying Project'
                sh 'rm -rf node_modules'
                sh 'npm install'
                dir('android')
                {
                    sh 'source ~/.bash_profile'
                    sh 'echo Android Build Started'
                    sh 'bundle install'
                    sh 'bundle update fastlane'
                    sh 'bundle exec fastlane alpha'
                }
            }
        }
    }
}