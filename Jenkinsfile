pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'feature-sonar', url: 'https://github.com/MaheshGit5096/Petclinic.git'
            }
        }
        stage('Build and Test') {
            steps {
                sh 'mvn clean install'
                sh 'mvn test'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh '''
                mvn sonar:sonar \
                -Dsonar.host.url=http://13.234.110.183:9000 \
                -Dsonar.login=34f741c0d428a964968acdca6777ee2f2777096d \
                -Dsonar.projectKey=Petclinic \
                -Dsonar.java.binaries=/home/ubuntu/project1/Petclinic/target/classes
                '''
            }
        }
        stage('Package') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
