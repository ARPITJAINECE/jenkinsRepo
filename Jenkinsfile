pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    sudo mkdir -p /var/www/html/website  # Create the directory if it doesn't exist
                    sudo cp -r ./index.html ./README.md /var/www/html/website/
                    sudo systemctl restart apache2  # Restart Apache to apply changes
                '''
            }
        }
    }
}
