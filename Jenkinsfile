node('fdf-node') {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    sh "pip3 install coverage"
    sh  "coverage run squareroot.py"
    sh  "coverage report -m"
    sh  "coverage xml "
    archiveArtifacts artifacts: 'coverage.xml'
    sh "cp ./coverage.xml ${env.WORKSPACE}/"
    def scannerHome = tool 'sonarscanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    
    }
  }
}
