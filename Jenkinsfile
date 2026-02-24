pipeline {
  agent any

  stages {
    stage('Append X') {
      steps {
        bat '''
          @echo off
          echo X>>"W:\\Downloads\\1.txt"
        '''
      }
    }
  }
}
