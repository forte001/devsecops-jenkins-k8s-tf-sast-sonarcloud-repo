pipeline {
    agent any
    tools { 
        maven 'Maven_3_9_9' 
    }
    stages {
        stage('Compile and Run Sonar Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_TOKEN', variable: 'SONAR_TOKEN')]) {
                    sh '''
                        mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar \
                        -Dsonar.projectKey=devsectest-org_devsectest-org \
                        -Dsonar.organization=devsectest_org \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
