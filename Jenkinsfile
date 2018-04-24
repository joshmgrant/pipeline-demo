#!/usr/bin/env groovy

node('master'){
  def branch = "${env.BRANCH_NAME}"

  echo branch

  stage('Checkout') {
    checkout scm
  }

  stage('Build') {
    sh 'npm install'
  }

  if(env.BRANCH_NAME == 'develop') {
    pushToCloudFoundry(
            target: 'api.run.pivotal.io',
            organization: 'pipeline_demos',
            cloudSpace: 'development',
            credentialsId: 'derek_pcf',
            manifestChoice: [manifestFile: 'config/dev/manifest.yml']
    )
  }
}
