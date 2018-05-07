// pipeline {
//   agent any
//   environment {
//     target_cluster = '10.65.182.142'
//   }
//   stages {
//     stage('start') {
//         agent any
//         steps {
//           script {

//             try {
//     //        build (job: 'start_job', propagate: true)
//     //        build job: 'start_job'
//               sh '''set +e

//         ssh root@$target_cluster -t "pytest -s /var/Nightswatch/jenkins_pipeline_tests/start.py" '''
//               currentBuild.result = 'SUCCESS'
//             } catch(e) {
//               currentBuild.result = "FAILURE"
//             }
//         }
//       }
//     }

//     stage('print_target_cluster') {
//       agent any
//       steps {
//         sh '''echo $target_cluster'''

//       }
//     }

//   }
// }

def BuildJob(projectName) {
    try {
       stage(projectName) {
         node {      
           def res = build job:projectName, propagate: false
           result = res.result
           if (result.equals("SUCCESS")) {
           } else {
              error 'FAIL' //sh "exit 1" // this fails the stage
           }
         }
       }
    } catch (e) {
        currentBuild.result = 'UNSTABLE'
        result = "FAIL" // make sure other exceptions are recorded as failure too
    }
}

node {
    BuildJob('start_job')
    stages {
      stage('print_target_cluster') {
        agent any
        steps {
          sh '''echo $target_cluster'''

        }
      }
    }
}