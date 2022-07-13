pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GithubCredentials', url: 'https://github.com/Lina-Lisa/myInfra2021Repo']]])
            }
        }
        
    stage('Terraform init'){
        steps{
            sh ('terraform init -reconfigure')
        }
    }
    
    stage ('Terraform Plan'){
        steps{
            sh('terraform plan')
     }
    }
    
    stage('Terraform Action'){
        steps{
            echo 'Terraform Action is -->${Action}'
            sh('terraform ${Action} --auto-approve')
        }
    }
  }
}
