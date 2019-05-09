//
node {
  stage('checkout sources') {
        // You should change this to be the appropriate thing
        git url: 'https://github.com/kellyth479/special-topics-labs-ci.git'
  }

  stage('Build') {
    // you should build this repo with a maven build step here
    echo "#########################################"
    echo "Here begins my code"
    echo "#########################################"
    sh 'mvn clean install'
  }
  try {
          stage('Test') {
              sh './gradlew check'
          }
      } finally {
          archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
          junit 'build/reports/**/*.xml'
      }

}
l