pipeline{
    agent{
        label 'Win'
    }
    tools{
        maven 'Maven'
    }
    stages{
        stage("Code Checkout")
        {
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/devops-example-projects/java-example.git'
            }
        }
        stage("Clean")
        {
            steps{
                bat 'mvn clean'
            }
        }
        stage("Compile")
        {
            steps{
                bat 'mvn compile'
            }
        }
        stage("Test")
        {
            steps{
                bat 'mvn test'
            }
        }
        stage("Publish Test Reports")
        {
            steps{
                junit 'target/test-reports/*.xml'
            }
        }
        stage("Package")
        {
            steps{
                bat 'mvn package'
            }
        }
        stage("Archieving Artifacts")
        {
            steps{
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
    }
}