pipeline{
  agent any
  stages {
    stage("checkout SCM"){
      steps{
        git branch:"master", url:"https://github.com/sandeepsirivella/big-o-performance-java.git"
      }
    }
    stage("build"){
      steps{
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage("unit test"){
      steps{
        sh 'npm test'
      }
    }
    stage('Docker build'){
      steps{
        sh """
        docker build -t madhu:1 .
        """
      }
    }
    stage("Deploy"){
      steps{
        script{
          sh """
             docker run -d -p 9020:80 --name ABC madhu:1
          """
      }
    }
  }
}
