        pipeline{
            tools{
                jdk 'java'
                maven 'maven'
            }
            agent none
            stages{
                stage('Checkout'){
                    agent any
                    steps{
                echo 'cloning...'
                        git 'https://github.com/theitern/DevOpsCodeDemo.git'
                    }
                }
                stage('Compile'){
                    agent any
                    steps{
                        echo 'compiling...'
                        sh 'mvn compile'
                }
                }
                stage('CodeReview'){
                    agent any
                    steps{
                    
                echo 'codeReview...'
                        sh 'mvn pmd:pmd'
                    }
                }
                stage('UnitTest'){
                    agent any
                    steps{
                    echo 'Testing'
                        sh 'mvn test'
                    }
                    post {
                    success {
                        junit 'target/surefire-reports/*.xml'
                    }
                }	
                }
                stage('Package'){
                    agent any
                    steps{
                        sh 'mvn package'
                    }
                }
            }
        }
