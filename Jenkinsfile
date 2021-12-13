pipeline {
  agent any
  stages {
    stage('Erik Build Stage') {
      steps {
        echo 'Erik stage 1. Build demo-app'
        bat(script: 'run_build_script.sh', encoding: 'UTF-8', label: 'Erik windows batch script', returnStatus: true)
      }
    }

  }
}