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
		deploy adapters: [tomcat9(credentialsId: 'cf964b00-46e6-49a8-a707-2c8bcb910caa', path: '', url: 'http://13.233.147.70:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
