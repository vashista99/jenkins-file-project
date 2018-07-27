pipeline {
    agent any

    stages {
        stage('Validate') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                 sh 'mvn validate'
                echo 'Building..'
            }
        }
        stage('Compile') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                sh 'mvn compile'
                echo 'Compileing'
            }
        }
        stage('Test') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                sh 'mvn test'
                                
                echo 'Testing'
            }
        }
        
        stage('Sonarqube') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                sh 'mvn sonar:sonar'
                echo 'Testing'
            }
        }
        stage('Package') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                sh 'mvn package'
                echo 'Packageing'
            }
        }
        // stage('Nexus') {
          //  steps {
            //    git 'https://github.com/vijaymargam/jenkins-file-project.git'
              //  sh 'mvn deploy'
                //echo 'Nexus'
           // }
        //}
        stage('Deploying') {
            steps {
                git 'https://github.com/vijaymargam/jenkins-file-project.git'
                sh 'mvn clean package'
                sh 'docker rm -f tomcat'
                sh 'docker build -t tomcat .'
                sh 'docker run --name tomcat -p 8080:8080 -dt tomcat'
                echo 'Deploying'
            }
        }
    }
}
