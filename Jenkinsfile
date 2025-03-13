pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {

        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/YosrBenAmor/Devops1'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean compile'
            }
        }

      /*  stage('Maven Clean Install') {
            steps {
                sh 'mvn clean install'
            }
        }*/
        stage('MVN Sonarqube') {
             steps {
                 sh 'mvn sonar:sonar  -Dsonar.token=sqa_d8e839e59109540e88a52e6f9c11cc093c9c1985 -Dmaven.test.skip=true'
             }
         }
         }

       /* stage('Building image') {
            steps {
                sh 'docker build -t yosrba/timesheet-devops:1.0.0 .'
            }
        }

        stage('Deploy Image') {
            steps {
                sh 'docker login'
                sh 'docker push yosrba/timesheet-devops:1.0.0'
            }
        }*/

        // stage('MVN Sonarqube') {
        //     steps {
        //         sh 'mvn sonar:sonar -Dsonar.token=squ_7af8e73dbed9867cd6208c11c6d5b0e6482c9be3 -Dmaven.test.skip=true'
        //     }
        // }
    }
}
