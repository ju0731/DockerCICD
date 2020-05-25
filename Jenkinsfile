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
        sh 'echo docker'
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