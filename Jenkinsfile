pipeline {
    agent any
    environment {
        PATH = "${env.PATH};C:\\apache-maven-3.9.9\\bin" // Update Maven path if necessary
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'master', url: 'https://github.com/mehtahetul/java_web_app.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube-25.2.0') {
                    bat 'mvn sonar:sonar -Dsonar.login=sqa_a2b30a21858c25656ec2af811eb4d463ad366ab8'
                }
            }
        }
        stage('Post Analysis') {
            steps {
                echo "SonarQube Analysis Complete"
            }
        }
         stage('Post Analysis') {
            steps {
                echo "SonarQube Analysis Complete"
            }
        }
    }
     post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs for more details.'
        }
    }
}
