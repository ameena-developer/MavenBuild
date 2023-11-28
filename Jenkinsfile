node(){

	def sonarHome = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
	 def mavenHome = tool name: 'MavenLatest', type: 'maven'
	
	stage('Code Checkout'){
		checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCreds', url: 'https://github.com/anujdevopslearn/MavenBuild']])
	}
	stage('Build Automation'){
		sh """
			ls -lart
			mvn clean install
			ls -lart target

		"""
	}
	
	stage('Code Scan'){
		 withSonarQubeEnv(credentialsId: 'SonarQubeToken') {
         sh "ls -lart ${sonarScanner}/bin/sonar-scanner"
		
	}
	
	stage('Code Deployment'){
		 deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://65.0.129.100:8080/')], contextPath: 'CounterApp', onFailure: false, war: 'target/*.war'
	}
}
