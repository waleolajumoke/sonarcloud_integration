pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=tech365app1 -Dsonar.organization=tech365app1 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=b8014450050f298ed041f022ab805d32530f975e'
			}
    }

// 	stage('RunSCAAnalysisUsingSnyk') {
//             steps {		
// 				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
// 					sh 'mvn snyk:test -fn'
// 				}
// 			}
//     }	

// // building docker image
// stage('Build') { 
//             steps { 
//                withDockerRegistry([credentialsId: "dockerlogin", url: ""]) {
//                  script{
//                  app =  docker.build("tech365image")
//                  }
//                }
//             }
//     }

// 	stage('Push') {
//             steps {
//                 script{
//                     docker.withRegistry("https://924338258393.dkr.ecr.us-east-2.amazonaws.com", "ecr:us-east-2:aws-credentials") 
// 			{
//                     app.push("latest")
//                     }
//                 }
//             }
//     	}


  }
}
