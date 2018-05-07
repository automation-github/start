pipeline {
  agent any
  environment {
    target_cluster = '10.65.182.142'
  }
  stages {
    stage('start') {
      agent any
      steps {
//        build (job: 'start_job', propagate: true)
        build job: 'start_job'
      }
    }

    stage('print_target_cluster') {
      agent any
      steps {
        sh '''echo $target_cluster'''

      }
    }

  }
}
