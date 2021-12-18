node('maven') {
    // some block
    stage('scm') {
    // some block
    git branch: 'main', url: 'https://github.com/surendradzelar/spring-petclinic.git'
}
stage('build') {
    // some block
    sh ''' sudo apt-get install maven -y
           mvn compile
           mvn package '''
}
stage('reports') {
    // some block
    archiveArtifacts artifacts: 'target/surefire-reports/.jar', followSymlinks: false
}
}
