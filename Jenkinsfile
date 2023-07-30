pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		      sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=slaysolutions_easybuggy -Dsonar.organization=slaysolutions -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=762f9c5763c203db0f5f2e450979bcef6a746162'
            }
        }
      stage('RunSCAAnalysisUsingSnyk') {
            steps {		
                  withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
                  sh 'mvn snyk:test -fn'
                  }
            }
      }
  }
}
