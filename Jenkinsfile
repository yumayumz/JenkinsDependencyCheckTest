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
        env.JAVA_HOME="$/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/"
        env.PATH="$/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
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
