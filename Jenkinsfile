node('MAVEN') {
    // some block
    stage('scm') {
    // some block
    git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
}
stage('build') {
    // some block
    sh ''' sudo apt-get install maven -y
           mvn complie
           mvn package '''
}
stage('reports') {
    // some block
    archiveArtifacts artifacts: 'target/surefire-reports/.jar', followSymlinks: false
}
}
