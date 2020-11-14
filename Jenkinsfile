pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git 'https://github.com/yumayumz/JenkinsDependencyCheckTest.git'
      }
    }

    stage('OWASP DependencyCheck') {
      steps {
        env.JAVA_HOME="${tool 'jdk1.8.0_272'}"
        env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
        dependencyCheck(additionalArguments: '--format HTML --format XML', odcInstallation: 'Default')
      }
    }

  }
  post {
    success {
      dependencyCheckPublisher(pattern: 'dependency-check-report.xml')
    }

  }
}
