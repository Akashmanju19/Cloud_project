pipeline{
    agent {
        node {
            label "valaxy"
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.8.7/bin:$PATH"
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
        withSonarQubeEnv('jenkins-connect') {    
            sh "${scannerHome}/bin/sonar-scanner"
        echo '<--------------- Sonar Analysis stopped  --------------->'
    }
}
}