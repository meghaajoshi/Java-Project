pipeline{
	agent any
	tools{
		maven 'local_maven'
	}
	stages{
		stage ('Build'){
			steps{
				sh 'mvn clean package'
			}
			post{
				success{
					echo "Archiving the artifacts"
					archiveArtifacts artifacts: '/webapps/.war'
				}
			}
		}
		stage ('Deploy to tomcat server'){
			steps{
				deploy adapters: [tomcat8(path: '', url: 'http://52.86.122.58:8090/')], contextPath: null, war: '/.war'
			}
		}
	}
	
		
}

