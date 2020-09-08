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