pipeline {
  agent any

  triggers {
    GenericTrigger(
      token: 'platformcore-backend',
      genericVariables: [
        [key: 'ref', value: '$.ref'],
        [key: 'projnamespace', value: '$.project.namespace'],
        [key: 'projectname', value: '$.project.name'],
        [key: 'triggeredby', value: '$.user_username'],
        [key: 'latestcommitid', value: '$.after']
      ],
      causeString: 'Triggered on $projnamespace - $projectname - $ref - $latestcommitid',
      printContributedVariables: true,
      printPostContent: true
    )
  }

  stages {

    stage('NPM Install') {
      steps {
        echo "Stage: NPM Install"
      }
    }

    stage('Build') {
      steps {
        echo "Stage: Build"
      }
    }

    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('SonarQube') {
          echo "Stage: SonarQube Analysis"
        }
      }
    }

    stage('Docker Build') {
      steps {
        echo "Stage: Docker Build"
      }
    }

  }
}

