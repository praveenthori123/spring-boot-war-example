pipeline{
    agent any
    tools {
        maven 'Maven'
        git 'Git'
    }
    stages{
        stage("Test"){
            steps{
                //mvn test
                sh "mvn test"
            }
           
        }
    stage("Build"){
            steps{
                sh "mvn install"
            }
           
        }
    stage("Deploy on test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://54.145.0.142:8080')], contextPath: '/app', war: '**/*.war'
            }
           
        }
    stage("Deploy on prod"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat_deployer', path: '', url: 'http://3.86.229.180:8080')], contextPath: '/app', war: '**/*.war'
            }
           
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
