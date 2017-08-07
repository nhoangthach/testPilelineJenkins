pipeline {
    agent {
        label "windows"
    }
	
	tools {
        maven 'Maven3.1.1'
        jdk 'java8'
    }

    stages {		
		stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }
		
        stage ('Compile Stage') {

            steps {
				bat 'mvn clean compile'
            }
        }
		
		stage ('Build Stage') {

            steps {
				bat 'mvn clean install'
            }
        }

        stage ('Testing Stage') {

            steps {
				bat 'mvn test'
            }
        }
		
		stage('Deploy Stage) {
            steps {
                sh 'mvn deploy'
            }
        }
    }
	
	post {
        always {
            archive 'target/*.jar'
        }
		
		failure {
            echo 'I failed :('
			mail from: 'nguyenhoangthach28@gmail.com',
			replyTo: 'fetel931408@gmail.com',
			to: 'nhoangthach@tma.com.vn',
            subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
            body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}