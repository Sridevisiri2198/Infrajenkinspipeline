pipeline {
    agent { label 'JAVA' }

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

        stage('Infra Scan (tfsec)') {
            steps {
                dir('tffiles') {
                    // Run tfsec, but do not fail the pipeline if issues are found
                    sh 'tfsec --soft-fail .'
                }
            }
        }

        stage('Lint (tflint)') {
            steps {
                dir('tffiles') {
                    sh 'tflint'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                dir('tffiles') {
                    // Save the plan to a file so apply uses the exact same actions
                    sh 'terraform plan -out=tfplan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                dir('tffiles') {
                    sh 'terraform apply -auto-approve tfplan'
                }
            }
        }
    }
}
