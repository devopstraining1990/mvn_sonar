pipeline{
    agent any
   
    stages 
    {
  
        stage("SCM") {
            steps {
              
                    git 'https://github.com/devopstraining1990/mvn_sonar.git'
                
            }
        }
   
    stage('Build Analysis') {
		steps {
			withSonarQubeEnv('sonar') {
				sh '/opt/maven/bin/mvn clean verify sonar:sonar '
			}
		}
	}
	stage("Quality Gate") {
            steps {
              timeout(time: 2, unit: 'MINUTES') {
                waitForQualityGate abortPipeline: true
              }
            }
          }

    }
}
