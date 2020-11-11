pipeline {
  agent {
    docker {
      image 'my-molecule:latest'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {

    stage ('Display versions') {
      steps {
        sh '''
          ls
          pwd
          ls -la /
          mkdir /.ansible         
          docker -v
          python3 -V
          ansible --version
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
