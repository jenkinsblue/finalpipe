pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        git(url: 'https://github.com/carreerit/mavenrepo.git', branch: 'master')
        sh 'mvn clean compile package deploy'
        sh 'echo URL=`cat /var/lib/jenkins/jobs/jenkinsblue/jobs/finalpipe/branches/master/builds/$BUILD_ID/log|grep Uploading |grep war |awk \'{print $2}\'` >/tmp/env'
      }
    }
    stage('Deploy DEV') {
      steps {
        build 'rundeck1'
      }
    }
    stage('QA') {
      steps {
        sh '''curl -s http://130.211.220.3:8080/student/ |grep 'Student Name'
if [ $? -ne 0 ]; then 
exit 1
fi'''
      }
    }
    stage('Approval') {
      steps {
        input 'Do you want to deploy to PROD'
      }
    }
  }
}