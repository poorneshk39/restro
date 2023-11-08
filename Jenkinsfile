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
		deploy adapters: [tomcat9(credentialsId: 'be577168-cb31-4bd3-aafc-2c7479dc0acc', path: '', url: 'http://13.233.147.70:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
