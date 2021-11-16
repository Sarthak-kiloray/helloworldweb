
node ('buildserver') {

  stage ('SCM_checkout') {
    checkout([$class: 'GitSCM',
        branches: [[name: '*/master']],
        extensions: [],
        userRemoteConfigs: [[credentialsId: 'plusforum',
        url: 'https://github.com/ganeshhp/helloworldweb.git']]])
  stage ('scm_checkout') {  
    checkout([$class: 'GitSCM', 
            branches: [[name: '*/master']], 
            extensions: [], 
            userRemoteConfigs: [[url: 'https://github.com/ganeshhp/Maven-petclinic-project.git']]])
  }

  stage ('maven_build') {
      sh 'mvn clean install'
  stage ('build') {
    sh 'mvn clean install'
  }

  input 'Proceed with Deployment?'

  input 'Proceed or Abort'
  stage ('artifactory') {
     sh 'curl -uganeshhp@gmail.com:AP4g3Wxp8znReDy8f3eVsSqDRjE -T target/petclinic.war "https://plussforum.jfrog.io/artifactory/petclinic-generic-local/petclinic.war"'
  }

  stage ('archive') {
    archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
  }
}
