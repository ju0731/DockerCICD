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
echo dockervar.json
docker login --username "${username}" --password "${password}"
./packer build ./DockerCICD_master/packer/makeDocker.json
'''
      }
    }

    stage('Create ECS') {
      steps {
        sh 'aws ecs create-cluster --cluster-name obd-docker-cluster-hanju'
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