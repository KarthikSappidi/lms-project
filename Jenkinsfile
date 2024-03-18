pipeline {
    agent any

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
                withSonarQubeEnv('sonar-server') {
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
        stage("Docker Build & Push") {
            steps {
                script {
                    withDockerRegistry(credentialsID: 'docker', toolname: 'docker') {
                        sh "cd api && docker build -t karthiksappidi/lms-public-api ."
                        sh "docker push karthiksappidi/lms-public-api"
                        sh "cd webapp && docker build -t karthiksappidi/lms-web ."
                        sh "docker push karthiksappidi/lms-web"
                    }
                }
            }
        }
        stage("Deploy to Container") {
            steps {
                script {
                    sh "docker-compose up -d"
                }
            }
        }
    }
}

    