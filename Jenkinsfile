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
                dir('Infrajenkinspipeline') {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Validate') {
            steps {
                dir('Infrajenkinspipeline') {
                    sh 'terraform validate'
                }
            }
        }

        stage('Terraform Format') {
            steps {
                dir('Infrajenkinspipeline') {
                    sh 'terraform fmt'
                }
            }
        }

        stage('Infra Scan') {
            steps {
                dir('Infrajenkinspipeline') {
                    // Use tfsec to scan Terraform code for security issues
                    sh 'tfsec .'
                }
            }
        }

        stage('Lint') {
            steps {
                dir('Infrajenkinspipeline') {
                    // Use tflint to check Terraform best practices
                    sh 'tflint'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                dir('Infrajenkinspipeline') {
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                dir('Infrajenkinspipeline') {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }
}
