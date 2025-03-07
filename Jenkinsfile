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

        // stage('MVN Nexus') {
        //     steps {
        //         sh 'mvn deploy -Dmaven.test.skip=true'
        //     }
        // }

        stage('Building Image') {
            steps {
                sh 'docker build -t yosrba/timesheet-devops:1.0.0 .'
            }
        }

        stage('Deploy Image') {
            steps {
                script {
                    // Login to Docker Hub and push the image
                    sh '''docker login -u yosrba -p ${DOCKER_PASSWORD}
                          docker push yosrba/timesheet-devops:1.0.0'''
                }
            }
        }

        /* stage('MVN Sonarqube') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.token=sqa_d8e839e59109540e88a52e6f9c11cc093c9c1985 -Dmaven.test.skip=true'
            }
        } */
    }
}
