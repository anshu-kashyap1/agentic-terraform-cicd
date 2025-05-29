pipeline {
  agent any

  tools {
    terraform 'Terraform-plugin'  // 👈 Name must match what's defined in Jenkins > Global Tool Configuration
  }

  environment {
    TF_VAR_region = 'ap-south-1'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Terraform Init') {
      steps {
        sh 'terraform init'
      }
    }

    stage('Terraform Plan') {
      steps {
        sh 'terraform plan -out=tfplan'
      }
    }

    stage('Terraform Apply') {
      steps {
        sh 'terraform apply -auto-approve tfplan'
      }
    }
  }
}
