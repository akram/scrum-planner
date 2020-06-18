openshift.withCluster() {
  env.NAMESPACE =  openshift.project()
  env.APP_NAME = "${env.JOB_NAME}".replaceAll(/-?${NAMESPACE}-?/, '').replaceAll(/-?pipeline-?/, '').substring(1)
}

pipeline {
  agent { label 'nodejs12' }
  stages {
    stage('Code Checkout') {
      steps {
        git url: "https://github.com/akram/scrum-planner"
      }
    }

    stage('Code Build') {
      steps {
        sh '''
           git clone https://github.com/akram/scrum-planner
           cd scrum-planner
           node --version
           npm --version
           npm install
           '''
      }
    }
  }
}
