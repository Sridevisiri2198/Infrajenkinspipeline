pipeline {
    agent {
        label 'JAVA'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sridevisiri2198/Infrajenkinspipeline.git'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Format') {
            steps {
                sh 'terraform fmt'
            }
        }

        stage('Infra Scan') {
            steps {
                // 'terraform scan' is NOT a valid Terraform command.
                // You probably meant 'tfsec .' or 'terrascan scan .'
                sh 'tfsec .'
            }
        }

        stage('Lint') {
            steps {
                sh 'tflint'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
