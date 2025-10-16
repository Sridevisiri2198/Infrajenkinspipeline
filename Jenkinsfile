pipeline {
    agent {
        label 'JAVA'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git url: 'https://github.com/Sridevisiri2198/Infrajenkinspipeline.git', branch: 'main'
            }
        }

        stage('Terraform Init') {
            steps {
                dir('tffiles') {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Validate') {
            steps {
                dir('tffiles') {
                    sh 'terraform validate'
                }
            }
        }

        stage('Terraform Format') {
            steps {
                dir('tffiles') {
                    sh 'terraform fmt'
                }
            }
        }

        stage('Infra Scan') {
            steps {
                dir('tffiles') {
                    // Use tfsec to scan Terraform code for security issues
                    sh 'tfsec .'
                }
            }
        }

        stage('Lint') {
            steps {
                dir('tffiles') {
                    // Use tflint to check Terraform best practices
                    sh 'tflint'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                dir('tffiles') {
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                dir('tffiles') {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
