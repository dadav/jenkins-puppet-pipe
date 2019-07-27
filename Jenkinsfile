pipeline {
  agent none

  stages {
    stage('pkd validate') {
      agent {
        docker {
          image 'puppet/puppet-dev-tools'
        }
      }
      steps {
        sh 'ls -l'
        sh 'MODULE_NAME="$(dirname $(tar tf module.tar.gz | head -1))" && tar xf module.tar.gz && cd $MODULE_NAME'
        sh 'pdk validate --parallel'
      }
    }
  }
}
