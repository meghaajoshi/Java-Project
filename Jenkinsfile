pipeline{
	agent any
	
	stages{
		stage ('Build'){
			steps{
				sh 'mvn clean package'
			}
			post{
				success{
					echo "Archiving the artifacts"
					archiveArtifacts artifacts: '/opt/apache-tomcat-8.5.85/webapps'
				}
			}
		}
		stage ('Deploy to tomcat server'){
			steps{
				deploy adapters: [tomcat8(path: '', url: 'http://52.86.122.58:8090/')], contextPath: null, war: '**/*.war'
			}
		}
	}
	
		
}

