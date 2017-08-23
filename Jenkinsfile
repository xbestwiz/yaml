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
            sh 'echo ${env.var1}'
            
          }
        )
      }
    }
  }
  environment {
    var1 = 'a'
    var2 = 'b'
  }
}