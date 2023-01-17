@Library('Santu_SharedLibraries') _

pipeline {
    agent any
    tools{
        maven "maven1"
        sonarQube "sonar"
    }

    stages {
        stage('Build and package war file') {
            steps {
                script{
                    buildWar()
                }  
            }
        }
    
        stage('Sonar QG'){
            steps{
                script{
                    
                    sonarQubeEnv(sonarQube)
                    sonarQuality()
                    
                }                             
                
            }
        }
        stage('Build Docker image'){
            steps{
                script{
                    buildDockerImage("santu458/santuproject099")                
                }
            }
        }
        stage('uploadNexus'){
            steps{
                script{
                    uploadNexus() 
                 }
            }
        }                 
    }
}
