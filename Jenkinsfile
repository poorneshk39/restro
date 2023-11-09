node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/poorneshk39/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			bat '"C:/maven/apache-maven-3.9.5/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: '1102caf5-53f2-470c-b5bf-f5871f207df0', path: '', url: 'localhost:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
