pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm 123
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the static website files to the Apache server
                sh '''
                    # Create the directory for the website if it doesn't exist
                    sudo mkdir -p /var/www/html/website

                    # Copy the static website files to the Apache document root
                    sudo cp -r ./index.html ./README.md /var/www/html/website/

                    # Restart Apache to apply changes
                    sudo systemctl restart apache2
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed. Check the logs for details.'
        }
    }
}
