pipeline {
    agent any

    environment {
        // Define any environment variables you might need
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${env.JAVA_HOME}/bin:${env.MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                // Build the application using Maven
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run unit tests
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Clean up workspace
            cleanWs()
        }
        success {
            // Notify success
            echo 'Build and test successful!'
        }
        failure {
            // Notify failure
            echo 'Build or test failed!'
        }
    }
}
