
node('master'){
  stage('scm_checkout'){
    checkout([$class: 'GitSCM', 
        branches: [[name: '*/master']], 
        extensions: [], 
        userRemoteConfigs: [[url: 'https://github.com/ganeshhp/Maven-petclinic-project.git']]])
    }
  stage('build'){
    sh 'mvn clean install'
    }
  stage('archive'){
    archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
   }
}

