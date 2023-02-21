pipeline{
    agent {
        node {
            label "valaxy"
        }
    }
    stages {
        stage('build') {
            steps{
                echo "------------ build started ---------"
                sh 'mvn clean install -Dmaven.test.skip=true'
                echo "------------ build completed ---------"
        }
        } 
    }
}
stage("Sonar Analysis"){
    environment{
        scannerHome = tool 'valaxy-sonarscanner'
    }
    steps{
        echo '<--------------- Sonar Analysis started  --------------->'
        withSonarQubeEnv('valaxy-sonarqube-server') {    
            sh "${scannerHome}/bin/sonar-scanner"
        echo '<--------------- Sonar Analysis stopped  --------------->'
    }
}
}