node('maven') {
    try{
        properties([parameters([choice(choices: ['scripted', 'main', 'declarative'], description: 'branch to build', name: 'BRANCH_TO_BUILD')])])
        // some block
    stage('scm') {
    // some block
    git url: 'https://github.com/surendradzelar/spring-petclinic.git', branch: "${params.BRANCH_TO_BUILD}"
}
stage('build') {
    // some block
    sh ''' echo "M2_HOME=${M2_HOME}"
           echo "JAVA_HOME=${JAVA_HOME}"
           echo "PATH=${PATH}"
           '''
           sh '/usr/local/Apache-Maven-3.6.3/bin/mvn clean package'
    sh ''' sudo apt-get install maven -y
           mvn compile
           mvn package '''
}

stage('archive reports') {
    // some block
    archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
}
stage ('publish test reports'){
    junit '**/TEST-*.xml'
}
currentBuild.result= 'SUCCESS'
    }
    catch (err) {
        currentBuild.result ='FAILURE'
    }
    finally{
        mail to 'surendradudi331@gmail.com'
        subject: "status of the pipeline: ${currentBuild.fullDisplayName}"
        body: "${env.BUILD_URL} has result ${currentBuild.result}"
    }
}
