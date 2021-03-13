pipeline {
    agent any
    stages {
        stage('build') {
            steps {
               // sh 'mvn --version'
               sh 'mvn clean install -DskipTests'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }
	stage('package') {
            steps {
                sh 'docker build -t eknaprasath/tomcat-sample:${BUILD_ID} .'
            }
		}
	stage('image-push') {
            steps {
                sh 'docker push eknaprasath/tomcat-sample:${BUILD_ID}'
            }
        }
    }
}
