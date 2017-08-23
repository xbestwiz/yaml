pipeline {
  agent any
  stages {
    stage('stage1') {
      steps {
        parallel(
          "stage1": {
            echo 'hello'
            
          },
          "stage2": {
            sleep 1
            
          }
        )
      }
    }
    stage('stage3') {
      steps {
        echo '${env.var1}'
      }
    }
    stage('stage4') {
      steps {
        stepcounter(outputFile: 'count.txt', outputFormat: 'json')
      }
    }
  }
  environment {
    var1 = 'a'
    var2 = 'b'
  }
}