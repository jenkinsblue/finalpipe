pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        git(url: 'https://github.com/carreerit/mavenrepo.git', branch: 'master')
        sh 'mvn clean compile package deploy'
      }
    }
  }
}