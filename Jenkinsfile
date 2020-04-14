pipeline{

 
agent any

 
tools{

 
maven 'Maven'
}


 environment {
    registry = "priyachaudhary477/docker_477"
    registryCredential = 'Docker'
}

 


 
stages {

 
stage("Code Checkout") {

 
steps {

 
git branch: 'master',

 
url: 'https://github.com/priyarani477/SampleJUnitTest.git'


 
}

 
}

 
stage('Build Stage')

 
{

 
steps{

 
bat 'mvn package'

 
}

 
}

 
stage('Compile Stage')

 
{

 
steps{

 
bat 'mvn clean compile'

 
}

 
}

 
stage('Testing Stage')

 
{

 
steps{

 
bat 'mvn test'

 
}

 
}

 
stage('build && SonarQube analysis')

 
{

 
steps {

 
withSonarQubeEnv('sonar_qube') {

 
bat 'mvn clean package sonar:sonar'

 
}

 
}

 
}

 
stage('Deploy artifact')
{
steps{

 bat 'mvn deploy'

}
}


stage('Building image') {
    steps{
      bat 'docker build -t springmvc .'
    }
  }
  stage('running container') {
    steps{
      bat 'docker run -p 80:8080 springmvc:latest'
    }
  }
  
  stage('Deploy Image') {
      steps{
        bat 'docker tag springmvc:latest priyachaudhary477/docker_477'
       bat 'docker push priyachaudhary477/docker_477'
       
        }
      }
      }
  
    
    




 
}
}
