pipeline {
    agent any
	tools { 
        maven 'Maven_3_8_5'  
    }

    stages {
        stage('CompileandRunSonarAnalysis') {
            steps {		
				bat("mvn -Dmaven.test.failure.ignore verify sonar:sonar -Dsonar.login=f357891511a76339f7c8701fdc543f062c755454 -Dsonar.projectKey=gcpvulnerableprojectkey -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=gcpsourcecodereposcan")
			}
        } 
		stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				bat("mvn snyk:test -fn")
			}
        } 
		stage('RunDASTUsingZAP') {
            steps {		
				bat("D:\\software\\ZAP\\zap.bat -cmd -quickurl https://www.example.com -quickprogress -quickout zap_report.html")
			}
        } 
    }
}