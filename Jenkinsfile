pipeline {
    agent {
        docker {
            // Jenkins will automatically pull this and spin it up
            image 'custom-jenkins-agent'
            
            // Mount the socket so the ephemeral agent can control the host Docker engine
            // Run as root to prevent permission issues mounting the workspace
            args '-v /var/run/docker.sock:/var/run/docker.sock -u root'
        }
    }
    stages {
        stage('Test Ephemeral Agent') {
            steps {
                sh 'echo "✅ Running inside an ephemeral container!"'
                sh 'docker --version'
                sh 'docker compose version'
            }
        }
    }
}