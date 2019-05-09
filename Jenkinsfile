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
    withMaven (maven: 'maven3') {
              sh "mvn package"
            }
  }
  try {
          stage('Test') {
              sh cd src
              sh './gradlew check'
          }
      } finally {
          //archiveArtifacts artifacts: '**/*.jar', fingerprint: true
          junit 'target/surefire-reports/*.xml'
      }

}