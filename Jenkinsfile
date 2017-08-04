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

        stage ('Testing Stage') {

            steps {
				bat 'mvn test'
            }
        }


        stage ('Deployment Stage') {
            steps {
				bat 'mvn deploy'
            }
        }
    }
}