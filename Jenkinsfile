pipeline {
    agent any
    environment {
        PATH = "${env.PATH};C:\\apache-maven-3.9.9\\bin" // Update Maven path if necessary
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo/project.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    bat 'mvn sonar:sonar -Dsonar.login=sqa_a2b30a21858c25656ec2af811eb4d463ad366ab8'
                }
            }
        }
        stage('Post Analysis') {
            steps {
                echo "SonarQube Analysis Complete"
            }
        }
    }
}
