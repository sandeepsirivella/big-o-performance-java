pipeline{
  agent any
  stages {
    stage("checkout SCM"){
      steps{
        git branch:"master", url:"https://github.com/sandeepsirivella/big-o-performance-java.git"
      }
    }
    stage("build"){
      step{
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage("unit test"){
      step{
        sh 'npm test'
      }
    }
    stage('Docker build'){
      step{
        sh """
        docker build -t madhu:1 .
        """
      }
    }
    stage("Deploy"){
      step{
        script{
          sh """
             docker run -d -p 9020:80 --name ABC madhu:1
          """
      }
    }
