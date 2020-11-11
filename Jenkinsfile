pipeline {
  agent {
    docker {
      image 'quay.io/ansible/molecule:3.1.5'
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
          molecule --version
        '''
      }
    }

    stage ('Molecule test') {
      steps {
        sh 'molecule lint'
      }
    }

  } // close stages
}   // close pipeline
