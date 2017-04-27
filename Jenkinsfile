pipeline {
  agent any
  stages {
    stage('Clone Beanstalk') {
      steps {
        build 'Webstack-Prod-To-Dev-Clone-Beanstalk'
      }
    }
    stage('Copy Data') {
      steps {
        parallel(
          "Copy DB": {
            build 'Webstack-Prod-To-Dev-Clone-Db'
            
          },
          "Copy Files": {
            build 'Webstack-Prod-To-Dev-Copy-Wpfiles'
            
          }
        )
      }
    }
    stage('Create Cache-Server') {
      steps {
        build 'Webstack-Dev-Varnish-Deploy'
      }
    }
  }
}