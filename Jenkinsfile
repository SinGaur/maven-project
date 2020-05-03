pipeline
{
agent any
	stages
{

		stage ('scm-checkout'){

			steps{

					git branch: 'master', url: 'https://github.com/SinGaur/maven-project' 
				}


		}
		stage ('compile'){

			steps{

					withMaven(jdk: 'localjdk', maven: 'localmaven') {
					sh 'mvn compile' 
					}
				}
		}
		stage ('test'){
			steps{
			withMaven(jdk: 'localjdk', maven: 'localmaven') {
				sh 'mvn test'
			}
			}
		}
		stage ('build'){
			steps{
			withMaven(jdk: 'localjdk', maven: 'localmaven') {
				sh 'mvn package'
			}
			}
		}
		stage ('deploy'){
			steps{
			sshagent(['deploy_tomcat']) {
				sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven-pipeline-job/webapp/target/webapp.war ec2-user@172.31.76.107:/var/lib/tomcat/webapps'
			}
			}
		}
   
}
}
