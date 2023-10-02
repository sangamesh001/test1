pipeline {
  agent any
  options {
    timeout(time: 1, unit: 'HOURS')
  }
  triggers {
    pollSCM('25 12 * * *')
  }
  stages{
    stage('vcs') {
        steps {
            git url: 'https://github.com/sangamesh00/test1.git',
                branch: 'main'
        }
    }
    stage('build') {
        steps {
            sh script: '/usr/share/maven/apache-maven-3.9.4/bin/mvn package'
        }
    }
    stage('test11') {
        steps {
            junit testResults: '**/surefire-reports/TEST-*.xml'
        }
    }
    stage('artifact'){
        steps {
            archiveArtifacts artifacts: '**/*.jar'
        }
    }
  }
  
}