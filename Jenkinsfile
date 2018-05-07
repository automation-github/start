pipeline {
  agent any
  environment {
    target_cluster = '10.65.182.142'
  }
  stages {
    stage('start') {
        agent any
        steps {
          script {

            try {
    //        build (job: 'start_job', propagate: true)
    //        build job: 'start_job'
              sh '''set +e

        ssh root@$target_cluster -t "pytest -s /var/Nightswatch/jenkins_pipeline_tests/start.py" '''
              currentBuild.result = 'SUCCESS'
            } catch(e) {
              currentBuild.result = "FAILURE"
            }
        }
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
