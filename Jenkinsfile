pipeline {
    agent any
    
    options {
        buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
    }
 
     stage('unit Test') {
            steps {
                sh 'ant -f test.xml -v'
                junit 'reports/results.xml'
            }
        }

    }
 
 
    stages {
        stage('build') {
            steps {
                sh 'ant -f build.xml -v'
            }
        }



    post {
        always {
            archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
        }
    }    
}
