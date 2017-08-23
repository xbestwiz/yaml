pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        echo 'hello'
      }
    }
    stage('stage3') {
      steps {
        parallel(
          "stage3": {
            echo '${env.var1}'
            
          },
          "stage2": {
            sh 'echo ${var1}'
            
          }
        )
      }
    }
    stage('statge4') {
      steps {
        retry(count: 3) {
          sleep 1
        }
        
      }
    }
  }
  environment {
    var1 = 'a'
    var2 = 'b'
  }
}