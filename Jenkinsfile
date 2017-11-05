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
    stage('playbook') {
      steps {
        ansiblePlaybook(playbook: '/etc/ansible/playbook.yml', dynamicInventory: true, startAtTask: 'whoami', sudo: true, sudoUser: 'root', forks: 2, colorized: true, inventoryContent: '#!/bin/env python #coding:utf8 import json import sys  def group():     host1 = [\'localhost\']     host2 = [\'192.168.33.100\']     group1 = \'g1\'     group2 = \'g2\'     hostdata = {         group1:{"hosts":host1},         group2:{"hosts":host2},     }     print(json.dumps(hostdata,indent=4))   if len(sys.argv) == 2 and (sys.argv[1] == \'--list\'):     group() else:     print("Usage: %s --list" % sys.argv[0])     sys.exit(1)')
      }
    }
  }
  environment {
    var1 = 'a'
    var2 = 'b'
  }
}