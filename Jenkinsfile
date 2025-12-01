pipeline {
  agent any

  stages {
   
   stage('clone project') {
      steps {
           git branch:'master' , url:'https://github.com/PraveenKuberABC/Amazon-Ecom.git'
       }
   }

   stage('clean') {
      steps {
           sh 'mvn clean'
       }
   }

   stage('compile') {
      steps {
           sh 'mvn compile'
       }
   }

   stage('test') {
      steps {
           sh 'mvn test'
       }
   }

   stage('build') {
      steps {
           sh 'mvn clean install'
       }
   }
  }
post {
  success {
    emailext( 
      subject: "Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
      body: "Hi Team,<br><br> The build completed successsfully.<br>Job: ${env.JOB_NAME} <br>Build number: #${env.BUILD_NUMBER}<br><br>regards,<br>Jenkins",
      recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
      to: "arpitha.abc.123@gmail.com"
      )
  }

  failure {
    emailext(
      subject: "Build Failure: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
      body: "Hi Team,<br><br> The build is failed.<br>Job : ${env.JOB_NAME} #${env.BUILD_NUMBER}<br><br>regards,<br>Jenkins",
      recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
      to: "arpitha.abc.123@gmail.com"
    )
  }
}
  
}
