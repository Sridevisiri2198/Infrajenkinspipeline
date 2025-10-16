pipeline{
    agent{
        label 'JAVA'
    }

    stages {
        stage('git checkout') {
            steps {
                git url:'https://github.com/Sridevisiri2198/Infrajenkinspipeline.git',
                branch:'main'
            }
        }
        stage('terraform init'){
            steps{
                sh 'terraform init'
            }
        }
        stage('terraform validate'){
            steps{
                sh 'terraform validate'
            }
        }
        stage('terraform format'){
            steps{
                sh 'terraform fmt'
            }
        }
        stage('infra scan'){
            steps{
                sh 'terraform scan'
            }
        }
        stage('lint'){
            steps{
                sh 'tflint'
            }
        }
        stage('terraform plan'){
            steps{
                sh 'terraform plan'
            }
        }
        stage('terraform apply'){
            steps{
                sh 'terraform apply -auto-approve'
            }
        }
    }
}