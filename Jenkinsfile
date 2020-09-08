pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Build Step'
      }
    }

    stage('run build') {
      parallel {
        stage('run build') {
          steps {
            sh 'sh build.sh'
            echo 'run build'
          }
        }

        stage('test shell') {
          steps {
            sh 'sh test.sh'
          }
        }
        post {
  always {
   archiveArtifacts(artifacts: 'target/demoapp.jar', fingerprint: true)
  }

failure {
      mail to: 'ci-team@example.com',
      subject: "Failed Pipeline ${currentBuild.fullDisplayName}",
      body: " For details about the failure, see ${env.BUILD_URL}"
     }
  }

      }
    }

    stage('deploy staging') {
      steps {
        echo 'deploy to staging'
        input 'can we deploy to staging?'
      }
    }

    stage('deploy production') {
      steps {
        echo 'deploy to production'
      }
    }

  }
}
