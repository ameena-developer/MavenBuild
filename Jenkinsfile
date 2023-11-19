node(){

	def sonarHome = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
	
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
		
		
	}
	
	stage('Code Deployment'){
		
	}
}
