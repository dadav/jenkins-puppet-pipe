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
          sh 'MODULE_NAME="$(dirname $(tar tf module.tar.gz | head -1))" && tar xf module.tar.gz && cd $MODULE_NAME'
          sh 'pdk validate --parallel'
        }
      }
        #stage('CHECK RPM') {
        #    agent {
        #        docker {
        #            image 'rpmbuild/centos7'
        #        }
        #    }
        #    steps {
        #        sh 'rpm -qlp module.rpm | wc -l | grep 1'
        #        sh 'rpm -qlp module.rpm | grep -P "^/opt/puppet-forge-modules/modules/[a-z]+"'
        #    }
        #}
    }
}
