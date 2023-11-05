pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Functionnal') {
          steps {
            sh 'dotnet test tests/FunctionnalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -O /var/aspnet'
      }
    }

  }
}