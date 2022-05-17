pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        build 'testmvn'
        sh '''
          mvn clean install
          docker build tag $BUILD_BUMBER .
          docker tag repo/imagename:$BUILD_BUMBER imagename:$BUILD_BUMBER
          docker login
          docker push repo/imagename:$BUILD_BUMBER 
        '''
      }
    }
    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }
  }
}
