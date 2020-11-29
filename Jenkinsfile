pipeline {
  agent {
    docker {
     image 'quay.io/ansible/molecule'
      args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {

    stage ('Display versions') {
      steps {
        sh '''
          docker -v
          python3 -V
          ansible --version
          molecule --version
        '''
      }
    }

    stage ('Molecule test') {
      steps {
        sh '''
          cd ./roles/tomcat/
          molecule test --all
        '''
      }
    }
  }
}
