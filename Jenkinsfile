pipeline {
  agent any
  stages {
    stage('Erik Build Stage') {
      steps {
        echo 'Erik stage 1. Build demo-app'
        bat(script: 'run_build_script.sh', encoding: 'UTF-8', label: 'Erik windows batch script', returnStatus: true)
      }
    }

    stage('Linux Tests Stage') {
      parallel {
        stage('Linux Tests Stage') {
          steps {
            echo 'Erik Step para Run linux tests'
            bat(script: 'run_linux_tests.sh', encoding: 'UTF-8', label: 'Step del tests stage', returnStatus: true)
          }
        }

        stage('Windows Test Stage') {
          steps {
            echo 'Erik Run windows tests'
          }
        }

      }
    }

    stage('Deploy in staging') {
      steps {
        echo 'Deploy to staging environment'
        input 'Is it OK to deploy to production?'
      }
    }

    stage('Deploy to PROD') {
      steps {
        echo 'Erik deploy to PROD'
      }
    }

  }
  post {
    always {
      archiveArtifacts(artifacts: 'target/demoapp.jar', fingerprint: true)
    }

    failure {
      mail(to: 'erik.estrada.job@hotmail.com', subject: "Erik Failed Pipeline ${currentBuild.fullDisplayName}", body: " For details about the failure, see ${env.BUILD_URL}")
    }

  }
}