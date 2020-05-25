pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        git(url: 'https://github.com/ju0731/DockerCICD.git', branch: 'master')
      }
    }

    stage('Make Docker') {
      steps {
        sh '''cd /var/lib/jenkins/workspace/
./packer build -var-file=var.json ./DockerCICD_master/packer/makeDocker.json'''
      }
    }

    stage('Create ECS') {
      steps {
        sh 'echo ecs'
      }
    }

    stage('Make Task') {
      steps {
        sh 'echo task'
      }
    }

    stage('Make Service') {
      steps {
        sh 'echo service'
      }
    }

  }
}