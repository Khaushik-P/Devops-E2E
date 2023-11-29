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
                dir('/var/lib/jenkins/workspace/Devops-E2E/mrdevops_java_app'){
                script{
                   mvnTest()
                }
                }
            }
            }
        }
}
