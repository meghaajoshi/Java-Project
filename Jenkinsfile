pipeline{
	agent any
	
	stages{
		stage ('Build'){
			steps{
				sh 'mvn clean package'
			}
			post{
				success{
					echo "Archiving the artufacts"
					archiveArtifacts artifacts: '**/target/*.war'
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

