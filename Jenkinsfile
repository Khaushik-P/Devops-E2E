@Library('my-shared-library') _

pipeline{
    agent any

    stages{
        stage('Git Checkout'){
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
            steps{
                script{
                   mvnTest()
                }
                }
            }
        
        stage('Integration test Maven'){
            steps{
                script{
                   mvnIntegration()
                }
                }
            }
            }
        }

