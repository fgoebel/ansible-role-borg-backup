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
          id
          echo $HOME         
          docker -v
          python3 -V
          ansible --version
          molecule --version
        '''
      }
    }

    stage ('Molecule test') {
      steps {
        sh 'sudo molecule test'
      }
    }

  } // close stages
}   // close pipeline
