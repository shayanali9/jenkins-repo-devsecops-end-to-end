pipeline {
    agent any
	tools { 
        maven 'Maven_3_8_5'  
    }

    stages {
        stage('CompileandRunSonarAnalysis') {
            steps {		
				//bat("mvn -Dmaven.test.failure.ignore verify sonar:sonar -Dsonar.login=89d87d7ec2e37aa36fad0ba3e6a2cd61c53aeebd -Dsonar.projectKey=simplemavenproject -Dsonar.host.url=http://127.0.0.1:9000/")
			}
        } 
		stage('RunSCAAnalysisUsingSnyk') {
            steps {		
		    //SNYK_TOKEN environment variable created on windows
				//bat("mvn snyk:test -fn ")
			}
        } 
		stage('RunDASTUsingZAP') {
            steps {		
				bat("D:\\software\\ZAP\\zap.sh -cmd -quickurl https://www.example.com -quickprogress -quickout D:\\software\\ZAP\\zap_report.html")
		  }
        } 
    }
	post {
        always {
            archiveArtifacts artifacts: 'zap_report.html', onlyIfSuccessful: true
        }
    }
}
