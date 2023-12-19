pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=tech365webapp -Dsonar.organization=tech365webapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=254a459ba65f0e4638b087116904f71411445d5f'
			}
    }

// 	stage('RunSCAAnalysisUsingSnyk') {
//             steps {		
// 				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
// 					sh 'mvn snyk:test -fn'
// 				}
// 			}
//     }	

// building docker image
stage('Build') { 
            steps { 
               withDockerRegistry([credentialsId: "dockerlogin", url: ""]) {
                 script{
                 app =  docker.build("tech365image")
                 }
               }
            }
    }

	stage('Push') {
            steps {
                script{
			
                    docker.withRegistry("https://924338258393.dkr.ecr.us-east-1.amazonaws.com", "ecr:us-east-1:aws-credentials") 
			{
                    app.push("latest")
                    }
                }
            }
    	}


  }
}
