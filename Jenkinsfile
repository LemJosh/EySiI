pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage ('Testing') {
            steps {
                // Show the installed version of JFrog CLI.
                jf '-v'
                
                // Show the configured JFrog Platform instances.
                jf 'c show'
                
                // Ping Artifactory.
                jf 'rt ping'
                
                // Create a file and upload it to a repository named 'my-repo' in Artifactory
                sh 'touch test-miggy-file'
                jf 'rt u test-miggy-file miggyrepo/'
                
                // Publish the build-info to Artifactory.
                jf 'rt bp'
            }
        }
    }
}
