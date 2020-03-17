pipeline {
    agent any
    options {
        timestamps()
        // This is to discard older builds and limit the number of artifacts that will be kept for a specific branch
        // (in Jenkins, not Artifactory).
        buildDiscarder(logRotator(
            numToKeepStr: (env.BRANCH_NAME ==~ "^master*" || env.BRANCH_NAME ==~ "^release*") ? '6' : (env.BRANCH_NAME =~ "^dev*") ? '3' : '5',
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
