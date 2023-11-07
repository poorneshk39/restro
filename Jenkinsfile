node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/poorneshk39/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: '53976350-f7bc-49cf-b8d6-43b229f2ed89', path: '', url: 'http://13.233.130.251:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}