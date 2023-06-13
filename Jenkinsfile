pipeline {
  agent {
    node {
      label 'Maven'
    }

  }
  stages {
    stage('Initialize') {
      steps {
        echo "PATH = ${M2_HOME}/bin:${PATH}"
        echo 'M2_HOME = /opt/maven'
      }
    }

    stage('Build') {
      steps {
        dir(path: '/var/lib/jenkins/workspace/New_demo/my-app') {
          sh 'mvn -B -DskipTests clean package'
        }

      }
    }

  }
  tools {
    maven 'MAVEN'
    jdk 'JDK'
  }
  post {
    always {
      junit(allowEmptyResults: true, testResults: '*/test-reports/.xml')
    }

  }
}