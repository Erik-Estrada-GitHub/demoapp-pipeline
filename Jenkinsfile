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

  }
}