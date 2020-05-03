pipeline
{
agent any
	stages
{

		stage ('scm checkout'){

			steps{

					git branch: 'master', url: 'https://github.com/SinGaur/maven-project' 
				}


		}
		stage ('compile source code'){

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
		stage ('package'){
			steps{
			withMaven(jdk: 'localjdk', maven: 'localmaven') {
				sh 'mvn package'
			}
			}
		}
   
}
}
