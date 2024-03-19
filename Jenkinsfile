pipeline {
    agent any

    environment {
        SCANNER_HOME = tool('sonar-scanner')
    }

    stages {
        stage("Clean Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout from Git") {
            steps {
                git branch: "dev", url: "https://github.com/KarthikSappidi/lms-project.git"
            }
        }
        stage("Soanr Analysis") {
            steps {
                withSonarQubeEnv('sonar-scanner') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=lms-project -Dsonar.projectKey=lms-project"
                }
            }
        }
        stage("Quality Gate") {
            steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsID: "Sonar-token"
                }
            }
        }
        stage("Build LMS") {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'docker', toolName: 'docker') {
                         echo "Building Artifacts..."
                sh "cd api && docker build -t karthiksappidi/lms-api ."
                sh "cd webapp && docker build -t karthiksappidi/lms-webapp ."
                sh "docker push karthiksappidi/lms-api"
                sh "docker push karthiksappidi/lms-webapp"
                     }
                }
            }
        }
    }
}

    
