pipeline {
  agent {
    docker {
      image 'quay.io/ansible/molecule'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {

    stage ('Display versions') {
      steps {
        sh '''
          ls
          docker -v
          python -V
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
