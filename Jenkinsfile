pipeline{
  agent any 
  tools {
    maven "maven3.9.8"
  }  
  stages {
    stage('1Code Checkout'){
      steps{
        sh "echo 'cloning the latest application version' "
        git branch: 'master', url: 'https://github.com/Rossiebee/maven-web-application.git'
      }
    }
    stage('2 Code Build'){
      steps{
        sh "echo 'running JUnit-test-cases' "
        sh "echo 'testing must pass to create artifacts ' "
        sh "mvn clean package"
        sh "mvn test"
      }
    }
    stage('3Checkstyle Analysis'){
      steps{
	sh 'mvn checkstyle:checkstyle'
/*			}
    stage('4CodeQuality'){
      steps{
        sh "echo 'Perfoming CodeQualityAnalysis' "
        sh "mvn sonar:sonar"
      }
    }

    stage('5uploadNexus'){
      steps{
        sh "mvn deploy"
      }
    } 
*/	      
   stage('6.ApprovaL Gate'){
     timeout(time:10, unit: 'HOURS'){
	input message: 'Application is ready for deployment, Please review and approve'
     }
   }
/*
   stage('8deploy2prod'){
      steps{
        deploy adapters: [tomcat8(credentialsId: 'tomcat-credentials', path: '', url: 'http://35.170.249.131:8080/')], contextPath: null, war: 'target/*war'
      }
    }
}
  post{
    always{
      emailext body: '''Hey guys
Please check build status.

Thanks
Landmark 
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
    }
    success{
      emailext body: '''Hey guys
Good job build and deployment is successful.

Thanks
Landmark 
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
    } 
    failure{
      emailext body: '''Hey guys
Build failed. Please resolve issues.

Thanks
Landmark 
+1 437 215 2483''', recipientProviders: [buildUser(), developers()], subject: 'success', to: 'paypal-team@gmail.com'
    }
  }
*/
}
