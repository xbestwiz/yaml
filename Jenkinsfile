pipeline {
  agent any
  stages {
    stage('stage1') {
      agent any
      steps {
        echo 'hello'
      }
    }
    stage('stage3') {
      parallel {
        stage('stage3') {
          steps {
            echo '${env.var1}'
            sh '''#!/bin/bash

echo \'This is a shell script.\''''
          }
        }
        stage('stage2') {
          steps {
            sh 'echo ${var1}'
          }
        }
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