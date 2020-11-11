pipeline {
  agent {
    docker {
      image 'quay.io/ansible/molecule:3.2.0a0'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {

    stage ('Display versions') {
      steps {
        sh '''
          ls
          pwd
          docker -v
          python3 -V
        '''
      }
    }

    stage ('Molecule test') {
      steps {
        sh 'sudo molecule lint'
      }
    }

  } // close stages
}   // close pipeline
