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
docker login
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
        sh 'aws ecs register-task-definition --cli-input-json file:///var/lib/jenkins/workspace/task.json'
      }
    }

    stage('Make Service') {
      steps {
        sh '''aws ecs create-service --cluster obd-docker-cluster-hanju --service-name fargate-service --task-definition sample-fargate:4 --desired-count 1 --launch-type "FARGATE" --network-configuration "awsvpcConfiguration={subnets=[subnet-0358ae653e4b4a215, 	
subnet-0b53fb891cb3041ce],securityGroups=[sg-038311bad06c0abb5],assignPublicIp=ENABLED}"'''
      }
    }

  }
}