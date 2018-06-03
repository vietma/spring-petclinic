pipeline {

	agent {
		label 'master'
	}
	
	tools {
		maven 'apache-maven-3.5.3'
		jdk 'jdk1.8.0_111'
	}
	
	stages {
		stage('Code Analysis') {
                        steps {
                                // Sonarqube 7 must be configured in the Jenkins Manage Jenkins -> Configure System -> Add SonarQube server 
                                withSonarQubeEnv('Sonar7.1') {
                                        bat "F:/1.DevOps/2018/sonar-scanner-3.2.0.1227-windows/bin/sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.login=4589cdd82528c33f782b63254d9656d564f42bd1 -Dsonar.projectVersion=1.0 -Dsonar.projectKey=PetClinic_Key_declarative -Dsonar.sources=src -Dsonar.java.binaries=."
                                }
                        }		
		}
		stage('Build') {
			steps {
                                // Execute Batch script if OS flavor is Windows		
                                bat(/"${mavenHome}\bin\mvn" clean package/)
                                // Publish JUnit Report
                                junit '**/target/surefire-reports/TEST-*.xml'			
			}		
		}
	}
}
