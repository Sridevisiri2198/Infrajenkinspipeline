pipeline {
    agent {
        label 'JAVA'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git url: 'https://github.com/Sridevisiri2198/Infrajenkinspipeline.git',  branch: 'main'
            }
        }

        stage('Terraform Init') {
            steps {
                dir(Infrajenkinspipeline) {
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
