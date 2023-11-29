@Library('my-shared-library') _

pipeline{
    agent any


    parameters{
        choice(name:'action' , choices:'create\ndelete', description: 'Choose create/Destroy')
        string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javapp')
        string(name: 'ImageTag', description: "tag of the docker build", defaultValue: 'v1')
        string(name: 'DockerHubUser', description: "name of the Application", defaultValue: 'khaushik')
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

        // stage('Static code Analysis: Sonarqube'){
        //     when{ expression { params.action == 'create'}}
        //     steps{
        //         script{
        //             def SonarQubecredentialsId = 'sonar-Api'
        //            staticCodeAnalysis(SonarQubecredentialsId)
        //         }
        //         }
        //     }
        stage('Maven Build'){
            when{ expression { params.action == 'create'}}
            steps{
                script{
                  mvnBuild()
                }
                }
            }
        stage('Docker image Build'){
            when{ expression { params.action == 'create'}}
            steps{
                script{
                   dockerBuild("${params.ImageName}","${params.ImageTag}","${params.AppName}"   )
                }
                }
            }
            }
        }

