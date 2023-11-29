@Library('my-shared-library') _

pipeline{
    agent any


    parameters{
        choices:(name:'action' , choices:'create\ndelete', description: 'Choose create/Destroy')
    }
    stages{
        stage('Git Checkout'){
            when{ expression { params.action == 'create'}}
            steps{
                script{
                   gitCheckout(
                     branch: 'main',
                      url: 'https://github.com/Khaushik-P/Devops-E2E.git'
                   )
                }
            }
            }
        stage('Unit test Maven'){
            when{ expression { params.action == 'create'}}
            steps{
                script{
                   mvnTest()
                }
                }
            }
        
        stage('Integration test Maven'){
            when{ expression { params.action == 'create'}}
            steps{
                script{
                   mvnIntegration()
                }
                }
            }
            }
        }

