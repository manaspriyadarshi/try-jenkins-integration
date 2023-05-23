node('fdf-node') {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    sh "pip3 install coverage"
    sh  "coverage  run -m unittest"
    sh  "coverage report -m"
    sh  "coverage xml "
    archiveArtifacts artifacts: 'coverage.xml'
    
    def scannerHome = tool 'sonarscanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    
    }
  }
}
