pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        git(url: 'https://github.com/carreerit/mavenrepo.git', branch: 'master')
        sh 'mvn clean compile package deploy'
        sh 'export URL=`cat /var/lib/jenkins/jobs/jenkinsblue/jobs/finalpipe/branches/master/builds/$BUILD_ID/log|grep Uploading |grep war |awk \'{print $2}\'`'
      }
    }
  }
}