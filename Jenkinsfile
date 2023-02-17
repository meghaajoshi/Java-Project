pipeline{
	agent any
	
	stages{
		stage ('Build'){
			steps{
				sh 'mvn clean package'
				post{
					success{
					     echo "archiving the artifacts"
					     archiveArtifacts artifacts: 'tomcat/webapps'
                			     remoteDirectory: '/opt/tomcat'
						
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

