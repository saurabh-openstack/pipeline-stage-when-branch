pipeline {
    agent any
    options {
        buildDiscarder(logRotator(
            numToKeepStr: 
            (env.BRANCH_NAME == "master") ? '6' : 
            (env.BRANCH_NAME == "^dev*") ? '3' : '5',
            artifactNumToKeepStr: '1',
            artifactDaysToKeepStr: '10'
        ))
    }
    stages {
        stage('Build Master') {
            when {
                branch 'master'
            }
            steps {
                echo 'Building master'
            }
        }
        stage('Build Dev') {
            when {
                branch 'dev'
            }
            steps {
                echo 'Building dev'
            }
        }
    }
}
