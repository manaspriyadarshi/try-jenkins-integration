node('fdf-node') {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    sh "pip3 install coverage"
    
    def scannerHome = tool 'sonarscanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
