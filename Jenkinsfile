pipeline {

    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {

        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/YosrBenAmor/Devops1.git'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('MVN Sonarqube') {
             steps {
                 sh 'mvn sonar:sonar  -Dsonar.token=sqa_d8e839e59109540e88a52e6f9c11cc093c9c1985 -Dmaven.test.skip=true'
             }
         }
         

        /* stage('MVN Sonarqube') {
            steps {
                sh 'mvn sonar:sonar  -Dsonar.token=sqa_d8e839e59109540e88a52e6f9c11cc093c9c1985 -Dmaven.test.skip=true'
            }
        }*/
        
    }
}
