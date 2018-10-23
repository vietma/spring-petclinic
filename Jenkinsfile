stage ('Compile') {
    node {
        git url: 'https://github.com/vietma/spring-petclinic.git'
        def mvnHome = tool 'Maven3.5.4'
        sh "${mvnHome}/bin/mvn -B compile"
    }
}

stage ('Test') {
    node ('WindowsNode') {
        git url: 'https://github.com/vietma/spring-petclinic.git'
        def mvnHome = tool 'Maven3.5.4'
        sh "${mvnHome}/bin/mvn -B verify"
        step([$class: 'ArtifactArchiver', artifacts: '**/target/*.war', fingerprint: true])
        step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
    }
}
